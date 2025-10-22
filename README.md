

Online Shop (Fake Store) 

A simple, responsive online shop frontend built with HTML, CSS, JavaScript and Bootstrap. Product data is fetched from the Fake Store API.


--- 

Table of Contents 

About 

Demo 

Features 

Technologies 

Getting Started 

Requirements 

Install / Run Locally


API Usage 

Example: Fetch Products


Project Structure 

Customization 

Contributing 

License 

Contact



--- 

About 

This project is a frontend-only online shop that displays product listings and details using the Fake Store API. It is intended as a lightweight example of an e‑commerce UI using modern frontend basics and Bootstrap for layout and responsiveness.


--- 

Demo 

You can run the project locally by opening index.html in your browser (see Getting Started). If hosted, the site renders product cards, product detail pages (or modals), and a simple cart UI (if implemented).


--- 

Features 

Fetches products from Fake Store API 

Responsive layout with Bootstrap 

Product listing and product detail view 

Search and/or category filters (optional) 

Add to cart UI (frontend only, optional) 

Clean, minimal UI suitable for learning and prototyping



--- 

Technologies 

HTML5 

CSS3 (custom styles) 

JavaScript (vanilla) 

Bootstrap (for grid, components, responsiveness) 

Fake Store API (for product data)



--- 

Getting Started 

Requirements 

A modern browser (Chrome, Firefox, Edge, Safari) 

No backend required — the app consumes the public Fake Store API 

(Optional) Live Server extension in VS Code for auto reload


Install / Run Locally 

1. Clone or download the repository to your machine.


2. Open the project folder.


3. Open index.html in your browser: 

Double-click index.html, or 

Use VS Code Live Server (Right click -> Open with Live Server), or 

Serve via a simple static server if you prefer.




No build steps required.


--- 

API Usage 

This project uses the Fake Store API. Basic endpoints: 

Get all products: https://fakestoreapi.com/products 

Get single product: https://fakestoreapi.com/products/{id} 

Get categories: https://fakestoreapi.com/products/categories 

Get products in a category: https://fakestoreapi.com/products/category/{category}


Example: Fetch Products (vanilla JS) 

Place this code in a script (for example in main.js) and call loadProducts() on page load. 

async function loadProducts() {
  const url = 'https://fakestoreapi.com/products';
  try {
    const res = await fetch(url);
    if (!res.ok) throw new Error('Network response was not ok');
    const products = await res.json();
    renderProducts(products); // implement this to show products in the DOM
  } catch (err) {
    console.error('Failed to load products:', err);
    // show a friendly message in the UI
  }
} 

function renderProducts(products) {
  const container = document.getElementById('products-container');
  container.innerHTML = '';
  products.forEach(p => {
    const card = document.createElement('div');
    card.className = 'col-md-4 mb-4';
    card.innerHTML = `
      <div class="card h-100">
        <img src="${p.image}" class="card-img-top p-3" alt="${p.title}" style="height:250px; object-fit:contain;">
        <div class="card-body d-flex flex-column">
          <h5 class="card-title">${p.title}</h5>
          <p class="card-text text-truncate">${p.description}</p>
          <div class="mt-auto d-flex justify-content-between align-items-center">
            <strong>$${p.price}</strong>
            <button class="btn btn-primary btn-sm">Add to cart</button>
          </div>
        </div>
      </div>
    `;
    container.appendChild(card);
  });
} 

// Call on page load
document.addEventListener('DOMContentLoaded', loadProducts);


--- 

Project Structure (suggested) 

/project-root
├─ index.html
├─ product.html        # optional: product details page
├─ css/
│  └─ styles.css
├─ js/
│  ├─ main.js
│  └─ api.js
├─ assets/
│  └─ images/
└─ README.md


--- 

Customization Tips 

Replace Fake Store API with your real API by swapping endpoints in api.js or main.js. 

Add local caching with localStorage to reduce calls while developing. 

Improve accessibility: add alt text, keyboard navigation, and ARIA attributes. 

Add a cart state (in localStorage) and show total items in the navbar.



--- 

Contributing 

If you or others want to improve the UI, add features, or fix bugs: 

1. Fork the repository.


2. Create a new branch: git checkout -b feature/my-feature


3. Make changes, commit: git commit -m "Add feature"


4. Push and open a Pull Request.




--- 

License 

Add your preferred license here (for example MIT). If you want, I can generate a short LICENSE file for MIT or another license.


--- 

Contact 

Created by Zahra Panahi— replace with your GitHub profile or email if you want to share contact info.


