---
title: HSHostingController, easily present fullscreen modals, safari, email, etc from SwiftUI
createdAt: 2020-05-13T07:30:22Z
---

# HSHostingController, easily present fullscreen modals, safari, email, etc from SwiftUI

```swift
import Foundation
import SwiftUI
import SafariServices
import MessageUI


class HSHosting {
    static var controller:UIViewController?
    static var nextModalPresentationStyle:UIModalPresentationStyle?
    
    static func openSafari(url:URL,tint:UIColor? = nil) {
        guard let controller = controller else {
            preconditionFailure("No controller present. Did you remember to use HSHostingController instead of UIHostingController in your SceneDelegate?")
        }
        
        let vc = SFSafariViewController(url: url)
        
        vc.preferredBarTintColor = tint
        //vc.delegate = self
        
        let topVC =  controller.hsTopController()
        topVC.present(vc, animated: true)
    }
    
    private static var mailDelegate = MailDelegate()
    static func sendEmail(to:[String],subject:String,body:String, isHtml:Bool = false) {
        guard let controller = controller else {
            preconditionFailure("No controller present. Did you remember to use HSHostingController instead of UIHostingController in your SceneDelegate?")
        }
        
        if MFMailComposeViewController.canSendMail() {
            
            let mail = MFMailComposeViewController()
            mail.mailComposeDelegate = mailDelegate
            mail.setToRecipients(to)
            mail.setMessageBody(body, isHTML: isHtml)
            mail.setSubject(subject)
            
            controller.hsTopController().present(mail, animated: true)
        } else {
            // show failure alert
        }
    }
}

class HSHostingController<Content> : UIHostingController<Content> where Content : View {
    
    override init(rootView: Content) {
        super.init(rootView: rootView)
        
        HSHosting.controller = self
    }
    
    @objc required dynamic init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    override func present(_ viewControllerToPresent: UIViewController, animated flag: Bool, completion: (() -> Void)? = nil) {

        if let nextStyle = HSHosting.nextModalPresentationStyle {
            viewControllerToPresent.modalPresentationStyle = nextStyle
            HSHosting.nextModalPresentationStyle = nil
        }

        super.present(viewControllerToPresent, animated: flag, completion: completion)
    }

}

private extension UIViewController {
    func hsTopController() -> UIViewController {
        if let navVC = self as? UINavigationController {
            return navVC.topViewController?.hsTopController() ?? navVC
        }
        
        if let presented = self.presentedViewController {
            return presented.hsTopController()
        }
        
        return self
    }
}

class MailDelegate:NSObject, MFMailComposeViewControllerDelegate {
    public func mailComposeController(_ controller: MFMailComposeViewController, didFinishWith result: MFMailComposeResult, error: Error?) {
        controller.dismiss(animated: true, completion: nil)
    }
}
```

https://gist.github.com/ConfusedVorlon/81dccc9ff2309f8c300e9ed8c42d0906