---
description: 'https://github.com/h5bp/Front-end-Developer-Interview-Questions'
---

# Interview Questions

## HTML Questions

Questions come from: [https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/src/questions/html-questions.md](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/src/questions/html-questions.md)

---

### **What does a doctype do?**

The doctype `<!DOCTYPE html>` is found at the very top of an HTML document, it's there for legacy reasons and is used to prevent the browser from entering in "Quirks Mode". There are 3 modes that browsers can operate: quirks mode, almost standards mode, and full standards mode. Quirks mode is a mode that the browser enters and the "layout emulates nonstandard behaviour in Navigator 4 and Internet Explorer 5". So, it's just not a good idea. Almost standards mode is when only some quirks are implemented. Full standards mode means that the browser will interpret HTML according to the specification.

References

* [https://html.spec.whatwg.org/multipage/syntax.html\#the-doctype](https://html.spec.whatwg.org/multipage/syntax.html#the-doctype)
* [https://developer.mozilla.org/en-US/docs/Glossary/Doctype](https://developer.mozilla.org/en-US/docs/Glossary/Doctype) 
* [https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks\_Mode\_and\_Standards\_Mode](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)

### 

### What are `data-` attributes good for?

`data-*` attributes are a way of adding arbitrary data to DOM elements and avoiding the use of invalid attributes. It can be useful for testing like adding a `data-testid="find-me"` in a tag and querying for it in a test. 

It can be accessed with JavaScript by reading the dataset property of the DOM element or by calling the getAttribute method:

```text
<article
  id="electric-cars"
  data-columns="3"
  data-index-number="12314"
  data-parent="cars">
...
</article>


const article = document.querySelector('#electric-cars');
 
article.dataset.columns // "3"
article.dataset.indexNumber // "12314"
article.dataset.parent // "cars"

article.getAttribute("data-columns") // "3"
```

Notice that the kebab case in the HTML is converted to camelCase in the dataset property. 

They can also be accessed from CSS:

```text
article[data-column="3"] { ... }
```

* Don't include content that should be visible in the page, because data- attributes are not accessible.
* It's possible to get the content of a data- attribute in CSS using  `attr(data-emoji)`

References

* [https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use\_data\_attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)
* [https://css-tricks.com/a-complete-guide-to-data-attributes/](https://css-tricks.com/a-complete-guide-to-data-attributes/)

