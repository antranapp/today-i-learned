---
title: Cypress.io - sitemap.xml validation test
createdAt: 2021-04-03T14:55:06Z
---

# Cypress.io - sitemap.xml validation test

```
describe('Sitemap', () => {
  let urls = [];

  before(() => {
    cy.request('sitemap.xml')
    .as('sitemap')
    .then((response) => {
      urls = Cypress.$(response.body)
            .find('loc')
            .toArray()
            .map(el => el.innerText);
    });
  });

  it('should succesfully load each url in the sitemap', () => {
    urls.forEach(cy.visit);
  });
});
```

---
https://stackoverflow.com/questions/55100545/cypress-io-sitemap-xml-validation-test