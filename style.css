let links = JSON.parse(localStorage.getItem("links")) || [];

function addLink() {
  const title = document.getElementById("title").value.trim();
  const url = document.getElementById("url").value.trim();
  const category = document.getElementById("category").value;
  const expiry = document.getElementById("expiry").value;

  if (!title || !url || !category || !expiry) {
    alert("Please fill out all fields correctly.");
    return;
  }

  const newLink = {
    id: Date.now(),
    title,
    url,
    category,
    expiry
  };

  links.push(newLink);
  localStorage.setItem("links", JSON.stringify(links));

  document.getElementById("title").value = "";
  document.getElementById("url").value = "";
  document.getElementById("category").value = "";
  document.getElementById("expiry").value = "";

  renderLinks();
}

function deleteLink(id) {
  links = links.filter(link => link.id !== id);
  localStorage.setItem("links", JSON.stringify(links));
  renderLinks();
}

function getStatus(expiry) {
  const now = new Date();
  const expDate = new Date(expiry);
  const diff = expDate - now;

  if (diff <= 0) return "expired";
  if (diff <= 3 * 24 * 60 * 60 * 1000) return "expiring";
  return "active";
}

function getCountdown(expiry) {
  const now = new Date();
  const expDate = new Date(expiry);
  const diff = expDate - now;

  if (diff <= 0) return "Expired";

  const days = Math.floor(diff / (1000 * 60 * 60 * 24));
  const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
  const minutes = Math.floor((diff / (1000 * 60)) % 60);
  const seconds = Math.floor((diff / 1000) % 60);

  return `${days}d ${hours}h ${minutes}m ${seconds}s`;
}

function renderLinks() {
  const container = document.getElementById("linksContainer");
  container.innerHTML = "";

  links.forEach(link => {
    const status = getStatus(link.expiry);

    const card = document.createElement("div");
    card.className = `link-card ${status}`;

    card.innerHTML = `
      <h3>${link.title}</h3>
      <p>${link.category}</p>
      <a href="${link.url}" target="_blank">Open Link</a>
      <p><strong>Time Left:</strong> ${getCountdown(link.expiry)}</p>
      <button onclick="deleteLink(${link.id})">Delete</button>
    `;

    container.appendChild(card);
  });
}

setInterval(renderLinks, 1000);

renderLinks();
