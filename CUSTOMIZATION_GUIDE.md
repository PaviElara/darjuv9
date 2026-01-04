# 🚀 Advanced Customization Guide

## Changing Colors & Branding

### 1. Update Tailwind Config
Edit `tailwind.config.js`:

```javascript
theme: {
  extend: {
    colors: {
      primary: '#YOUR_LIGHT_COLOR',      // Background
      secondary: '#YOUR_MAIN_COLOR',      // CTA buttons
      accent: '#YOUR_ACCENT_COLOR',       // Highlights
      dark: '#YOUR_DARK_COLOR',           // Text
      light: '#YOUR_LIGHT_BG',            // Light background
    }
  }
}
```

### 2. Update Logo
In `FloatingNav.jsx`:
```javascript
<div className="text-2xl font-bold bg-gradient-to-r from-secondary to-accent bg-clip-text text-transparent">
  YOUR_BRAND_NAME  // Change this
</div>
```

### 3. Update Hero Image
In `HeroSection.jsx`:
```javascript
<img
  src="YOUR_IMAGE_URL"  // Change image
  alt="Your Product"
  className="rounded-3xl shadow-2xl w-full"
/>
```

---

## Adding New Products

### 1. Add to Products Array (Home.jsx)
```javascript
const [products] = useState([
  // ... existing products
  {
    id: 13,
    name: 'Your Product Name',
    image: 'https://images.unsplash.com/photo/....',  // Image URL
    price: 29.99,
    originalPrice: 39.99,  // Optional - for discounts
    description: 'Your product description here',
    category: 'Supplements',  // or 'Skincare', 'Wellness'
    rating: 4.8,
    reviews: 250,
    badge: 'New'  // Optional: 'New', 'Best Seller', 'Top Rated', 'Popular'
  }
])
```

### 2. Image Sources
Recommended free image sources:
- **Unsplash**: https://unsplash.com/
- **Pexels**: https://www.pexels.com/
- **Pixabay**: https://pixabay.com/
- **Shopify CDN**: For product images

---

## Customizing Navigation Items

### 1. Add New Nav Items
In `FloatingNav.jsx`, add to the nav items section:

```javascript
<motion.button 
  whileHover={{ scale: 1.1 }}
  className="flex items-center gap-2 hover:text-secondary transition"
>
  <YourIconComponent size={24} />
  <span className="text-sm font-medium">Your Item</span>
</motion.button>
```

### 2. Add New Categories
In `FloatingNav.jsx`, update categories array:

```javascript
const categories = [
  { id: 'all', label: 'All Products' },
  { id: 'skincare', label: 'Skincare' },
  { id: 'supplements', label: 'Supplements' },
  { id: 'wellness', label: 'Wellness' },
  { id: 'fitness', label: 'Fitness' },  // Add new
]
```

Then update the filter logic in `Home.jsx`:
```javascript
const filteredProducts = products.filter(product => {
  // ... existing logic
  const matchesCategory = selectedCategory === 'all' || 
                         product.category.toLowerCase() === selectedCategory.toLowerCase()
  return matchesSearch && matchesCategory
})
```

---

## Modifying Product Cards

### 1. Change Card Layout
In `ProductCard.jsx`, modify the grid structure:

```javascript
<motion.div className="grid grid-cols-1 gap-4">  // Adjust columns here
  {/* Card content */}
</motion.div>
```

### 2. Add New Product Fields
In `ProductCard.jsx`:

```javascript
<div className="text-sm text-gray-600 mb-4">
  {product.NEW_FIELD}  // Add your new field
</div>
```

Then add the field when creating products.

### 3. Customize Buttons
In `ProductCard.jsx`:

```javascript
<motion.button
  whileHover={{ scale: 1.02 }}
  whileTap={{ scale: 0.98 }}
  onClick={() => onAddToCart(product)}
  className="w-full bg-gradient-to-r from-secondary to-accent text-white py-3 rounded-xl font-bold hover:shadow-glow transition flex items-center justify-center gap-2"
>
  <AiOutlineShoppingCart size={20} />
  YOUR_BUTTON_TEXT  // Change this
</motion.button>
```

---

## Customizing Cart Drawer

### 1. Add Coupon Code Input
In `CartDrawer.jsx`, before checkout button:

```javascript
<div className="mb-4">
  <label className="block text-sm font-bold text-dark mb-2">Coupon Code</label>
  <input
    type="text"
    placeholder="Enter code"
    className="w-full px-4 py-2 border-2 border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-secondary"
  />
</div>
```

### 2. Add Tax Calculation
Update summary in `CartDrawer.jsx`:

```javascript
const tax = total * 0.1;  // 10% tax

<div className="flex justify-between text-sm">
  <span className="text-gray-600">Tax (10%)</span>
  <span className="font-bold">${tax.toFixed(2)}</span>
</div>

<span className="text-2xl font-bold text-secondary">
  ${(total + tax).toFixed(2)}
</span>
```

---

## Customizing Login Modal

### 1. Add Phone Number Field
In `LoginModal.jsx`:

```javascript
<div>
  <label className="block text-sm font-bold text-dark mb-2">Phone</label>
  <input
    type="tel"
    name="phone"
    value={formData.phone}
    onChange={handleChange}
    placeholder="(123) 456-7890"
    className="w-full px-4 py-3 bg-gray-100 rounded-lg focus:outline-none focus:ring-2 focus:ring-secondary transition"
  />
</div>
```

### 2. Add Social Login Options
In `LoginModal.jsx`, duplicate the Google button:

```javascript
<motion.button
  whileHover={{ scale: 1.02 }}
  whileTap={{ scale: 0.98 }}
  className="w-full flex items-center justify-center gap-3 border-2 border-gray-200 py-3 rounded-lg font-bold hover:border-secondary transition"
>
  <SocialIcon size={20} className="text-accent" />
  Continue with Provider
</motion.button>
```

---

## Animations & Effects

### 1. Change Animation Speeds
In `tailwind.config.js`:

```javascript
animation: {
  'fade-in': 'fadeIn 0.3s ease-in',  // Faster (was 0.5s)
  'slide-up': 'slideUp 0.8s ease-out',  // Slower (was 0.5s)
  'bounce-slow': 'bounce 3s infinite',
}
```

### 2. Add New Animation
In `index.css`:

```css
@keyframes yourAnimation {
  0% {
    /* Start state */
  }
  100% {
    /* End state */
  }
}
```

In `tailwind.config.js`:

```javascript
'your-animation': 'yourAnimation 1s ease-in-out'
```

### 3. Modify Hover Effects
In any component:

```javascript
<motion.button
  whileHover={{ scale: 1.15 }}  // Change scale value
  whileTap={{ scale: 0.90 }}    // Change tap scale
  transition={{ duration: 0.5 }}  // Change duration
>
  Button
</motion.button>
```

---

## Styling Customizations

### 1. Change Button Styles
In `index.css`:

```css
@layer components {
  .btn-primary {
    @apply px-8 py-4 bg-gradient-to-r from-secondary to-accent text-white rounded-full font-bold hover:shadow-glow transition;
  }
}
```

### 2. Modify Box Shadows
In `tailwind.config.js`:

```javascript
boxShadow: {
  'glass': '0 8px 32px 0 rgba(99, 102, 241, 0.5)',  // Adjust
  'glow': '0 0 30px rgba(99, 102, 241, 0.5)',  // Adjust
}
```

### 3. Update Rounded Corners
In `tailwind.config.js`:

```javascript
borderRadius: {
  'sm': '4px',
  'md': '8px',
  'lg': '12px',
  'xl': '16px',
  '2xl': '24px',
}
```

---

## Responsive Design Tweaks

### 1. Change Grid Columns
In `Home.jsx`:

```javascript
// Current: 1 col mobile, 2 tablet, 3 desktop, 4 XL
className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8"

// Make it 2 columns on mobile:
className="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4"
```

### 2. Adjust Padding
Change all `px-6` and `py-8` to your preference:

```javascript
// Smaller spacing:
className="px-4 py-6"

// Larger spacing:
className="px-8 py-12"
```

---

## Performance Optimizations

### 1. Add Image Lazy Loading
```javascript
<img
  src={product.image}
  alt={product.name}
  loading="lazy"  // Add this
  className="w-full h-full object-cover"
/>
```

### 2. Code Splitting (Create separate files)
```bash
# Create new component file for each section
src/components/PromoBanner.jsx
src/components/ReviewSection.jsx
src/components/FAQSection.jsx
```

### 3. Memoization
```javascript
export default memo(ProductCard)  // Prevent unnecessary re-renders
```

---

## API Integration Ready

### 1. Replace Products from API
In `Home.jsx`:

```javascript
useEffect(() => {
  fetch('YOUR_API_ENDPOINT/products')
    .then(res => res.json())
    .then(data => setProducts(data))
}, [])
```

### 2. Submit Form to Backend
In `LoginModal.jsx`:

```javascript
const handleSubmit = async (e) => {
  e.preventDefault()
  const response = await fetch('YOUR_API_ENDPOINT/login', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(formData)
  })
  // Handle response
}
```

---

## Environment Variables

Create `.env.local`:

```
VITE_API_URL=https://your-api.com
VITE_IMAGE_CDN=https://your-cdn.com
VITE_APP_NAME=Your App Name
```

Use in code:

```javascript
const API_URL = import.meta.env.VITE_API_URL
```

---

## Version Control

Recommended `.gitignore`:

```
node_modules/
.env.local
.env.*.local
dist/
.DS_Store
*.log
```

---

## Build & Deployment

### Build for Production
```bash
npm run build
```

### Preview Build
```bash
npm run preview
```

### Deploy to Netlify
```bash
npm run build
# Upload 'dist' folder to Netlify
```

### Deploy to Vercel
```bash
npm install -g vercel
vercel
```

---

Your website is now fully customizable! Happy building! 🚀
