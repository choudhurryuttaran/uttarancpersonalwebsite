// Smooth scroll for internal links
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener("click", function (e) {
    e.preventDefault();
    document.querySelector(this.getAttribute("href")).scrollIntoView({
      behavior: "smooth"
    });
  });
});

// Theme toggle button
const themeToggle = document.createElement("button");
themeToggle.innerText = "🌓 Theme";
themeToggle.style.position = "fixed";
themeToggle.style.bottom = "20px";
themeToggle.style.right = "20px";
themeToggle.style.padding = "10px 15px";
themeToggle.style.border = "none";
themeToggle.style.borderRadius = "8px";
themeToggle.style.background = "var(--accent)";
themeToggle.style.color = "#fff";
themeToggle.style.cursor = "pointer";
themeToggle.style.zIndex = "1000";
document.body.appendChild(themeToggle);

themeToggle.addEventListener("click", () => {
  if (document.documentElement.getAttribute("data-theme") === "dark") {
    document.documentElement.removeAttribute("data-theme");
    localStorage.removeItem("theme");
  } else {
    document.documentElement.setAttribute("data-theme", "dark");
    localStorage.setItem("theme", "dark");
  }
});

// Apply saved theme on load
if (localStorage.getItem("theme") === "dark") {
  document.documentElement.setAttribute("data-theme", "dark");
}

// Scroll-to-top button
const scrollTopBtn = document.createElement("button");
scrollTopBtn.innerText = "⬆";
scrollTopBtn.style.position = "fixed";
scrollTopBtn.style.bottom = "70px";
scrollTopBtn.style.right = "20px";
scrollTopBtn.style.padding = "10px 15px";
scrollTopBtn.style.border = "none";
scrollTopBtn.style.borderRadius = "8px";
scrollTopBtn.style.background = "var(--primary)";
scrollTopBtn.style.color = "#fff";
scrollTopBtn.style.cursor = "pointer";
scrollTopBtn.style.zIndex = "1000";
scrollTopBtn.style.display = "none";
document.body.appendChild(scrollTopBtn);

// Show button when scrolling
window.addEventListener("scroll", () => {
  if (window.scrollY > 200) {
    scrollTopBtn.style.display = "block";
  } else {
    scrollTopBtn.style.display = "none";
  }
});

// Scroll to top on click
scrollTopBtn.addEventListener("click", () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
});
