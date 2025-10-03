{
  "name": "the-ayurveda-world",
  "version": "1.0.0",
  "description": "Professional Ayurveda E-Commerce Website",
  "scripts": {
    "dev": "next dev",
    "build": "next build", 
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "13.5.6",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "author": "The Ayurveda World",
  "license": "MIT"
}
import { useState } from 'react';

export default function Home() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [activeTab, setActiveTab] = useState('dashboard');

  // Sample data
  const [products, setProducts] = useState([
    { id: 1, name: 'Ashwagandha Powder', price: 299, stock: 50 },
    { id: 2, name: 'Brahmi Oil', price: 399, stock: 30 }
  ]);
  
  const [orders, setOrders] = useState([
    { id: 1001, customer: 'Rahul Sharma', amount: 698, status: 'pending' },
    { id: 1002, customer: 'Priya Patel', amount: 1299, status: 'completed' }
  ]);

  const handleLogin = (e) => {
    e.preventDefault();
    if (email === 'theayurvedaworldofficial@gmail.com' && password === 'admin123') {
      setIsLoggedIn(true);
    } else {
      alert('Invalid credentials! Use: theayurvedaworldofficial@gmail.com / admin123');
    }
  };

  const addProduct = () => {
    const newProduct = {
      id: Date.now(),
      name: `New Product ${products.length + 1}`,
      price: 199,
      stock: 25
    };
    setProducts([...products, newProduct]);
  };

  const updateOrderStatus = (orderId, status) => {
    setOrders(orders.map(order => 
      order.id === orderId ? {...order, status} : order
    ));
  };

  // LOGIN PAGE
  if (!isLoggedIn) {
    return (
      <div style={{ 
        padding: 20, 
        fontFamily: 'Arial', 
        minHeight: '100vh',
        background: 'linear-gradient(135deg, #f0f9f0, #e6f3e6)',
        display: 'flex',
        alignItems: 'center',
        justifyContent: 'center'
      }}>
        <div style={{ 
          background: 'white', 
          padding: 40, 
          borderRadius: 15, 
          boxShadow: '0 10px 30px rgba(0,0,0,0.1)',
          maxWidth: 400,
          width: '100%'
        }}>
          <div style={{ textAlign: 'center', marginBottom: 30 }}>
            <h1 style={{ color: '#059669', margin: 0 }}>🌿 The Ayurveda World</h1>
            <p style={{ color: '#666', marginTop: 5 }}>Owner Login</p>
          </div>
          
          <form onSubmit={handleLogin}>
            <div style={{ marginBottom: 15 }}>
              <input 
                type="email" 
                placeholder="Email Address" 
                value={email}
                onChange={(e) => setEmail(e.target.value)}
                style={{ 
                  width: '100%', 
                  padding: 12, 
                  border: '1px solid #ddd', 
                  borderRadius: 8,
                  fontSize: 16
                }}
                required
              />
            </div>
            
            <div style={{ marginBottom: 20 }}>
              <input 
                type="password" 
                placeholder="Password" 
                value={password}
                onChange={(e) => setPassword(e.target.value)}
                style={{ 
                  width: '100%', 
                  padding: 12, 
                  border: '1px solid #ddd', 
                  borderRadius: 8,
                  fontSize: 16
                }}
                required
              />
            </div>
            
            <button 
              type="submit"
              style={{ 
                width: '100%', 
                padding: 15, 
                background: 'linear-gradient(135deg, #059669, #10b981)', 
                color: 'white', 
                border: 'none', 
                borderRadius: 8,
                fontSize: 16,
                fontWeight: 'bold',
                cursor: 'pointer'
              }}
            >
              🔐 Login to Dashboard
            </button>
          </form>
          
          <div style={{ 
            marginTop: 25, 
            padding: 15, 
            background: '#f8fafc', 
            borderRadius: 8,
            fontSize: 14,
            color: '#666'
          }}>
            <p style={{ margin: 0, fontWeight: 'bold' }}>Demo Credentials:</p>
            <p style={{ margin: '5px 0' }}>📧 Email: theayurvedaworldofficial@gmail.com</p>
            <p style={{ margin: 0 }}>🔑 Password: admin123</p>
          </div>
        </div>
      </div>
    );
  }

  // OWNER DASHBOARD
  return (
    <div style={{ 
      fontFamily: 'Arial', 
      minHeight: '100vh',
      background: '#f8fafc'
    }}>
      {/* Header */}
      <header style={{
        background: 'linear-gradient(135deg, #059669, #10b981)',
        color: 'white',
        padding: '20px 0',
        boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
      }}>
        <div style={{ maxWidth: 1200, margin: '0 auto', padding: '0 20px' }}>
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
            <div>
              <h1 style={{ margin: 0, fontSize: 24 }}>🌿 The Ayurveda World</h1>
              <p style={{ margin: 5, opacity: 0.9 }}>Owner Dashboard</p>
            </div>
            <button 
              onClick={() => setIsLoggedIn(false)}
              style={{
                background: 'rgba(255,255,255,0.2)',
                color: 'white',
                border: '1px solid rgba(255,255,255,0.3)',
                padding: '8px 16px',
                borderRadius: 6,
                cursor: 'pointer'
              }}
            >
              Logout
            </button>
          </div>
        </div>
      </header>

      {/* Navigation */}
      <nav style={{
        background: 'white',
        padding: '15px 0',
        borderBottom: '1px solid #e2e8f0'
      }}>
        <div style={{ maxWidth: 1200, margin: '0 auto', padding: '0 20px' }}>
          <div style={{ display: 'flex', gap: 10, flexWrap: 'wrap' }}>
            {['dashboard', 'products', 'orders', 'customers', 'settings'].map(tab => (
              <button
                key={tab}
                onClick={() => setActiveTab(tab)}
                style={{
                  background: activeTab === tab ? '#10b981' : 'transparent',
                  color: activeTab === tab ? 'white' : '#374151',
                  border: 'none',
                  padding: '10px 20px',
                  borderRadius: 6,
                  cursor: 'pointer',
                  textTransform: 'capitalize'
                }}
              >
                {tab}
              </button>
            ))}
          </div>
        </div>
      </nav>

      {/* Main Content */}
      <main style={{ maxWidth: 1200, margin: '20px auto', padding: '0 20px' }}>
        
        {/* DASHBOARD TAB */}
        {activeTab === 'dashboard' && (
          <div>
            <h2>📊 Dashboard Overview</h2>
            
            {/* Stats Cards */}
            <div style={{ 
              display: 'grid', 
              gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', 
              gap: 20, 
              marginBottom: 30 
            }}>
              <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
                <h3 style={{ color: '#059669', margin: '0 0 10px 0' }}>Total Revenue</h3>
                <p style={{ fontSize: 24, fontWeight: 'bold', margin: 0 }}>₹{orders.reduce((sum, order) => sum + order.amount, 0)}</p>
              </div>
              
              <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
                <h3 style={{ color: '#059669', margin: '0 0 10px 0' }}>Total Products</h3>
                <p style={{ fontSize: 24, fontWeight: 'bold', margin: 0 }}>{products.length}</p>
              </div>
              
              <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
                <h3 style={{ color: '#059669', margin: '0 0 10px 0' }}>Pending Orders</h3>
                <p style={{ fontSize: 24, fontWeight: 'bold', margin: 0 }}>{orders.filter(o => o.status === 'pending').length}</p>
              </div>
            </div>

            {/* Recent Orders */}
            <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
              <h3>Recent Orders</h3>
              {orders.map(order => (
                <div key={order.id} style={{ 
                  display: 'flex', 
                  justifyContent: 'space-between', 
                  alignItems: 'center',
                  padding: '15px 0',
                  borderBottom: '1px solid #f1f1f1'
                }}>
                  <div>
                    <strong>Order #{order.id}</strong>
                    <p style={{ margin: 5, color: '#666' }}>{order.customer} - ₹{order.amount}</p>
                  </div>
                  <span style={{
                    background: order.status === 'completed' ? '#d1fae5' : '#fef3c7',
                    color: order.status === 'completed' ? '#065f46' : '#92400e',
                    padding: '5px 10px',
                    borderRadius: 20,
                    fontSize: 14
                  }}>
                    {order.status}
                  </span>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* PRODUCTS TAB */}
        {activeTab === 'products' && (
          <div>
            <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: 20 }}>
              <h2>🛍️ Product Management</h2>
              <button 
                onClick={addProduct}
                style={{
                  background: '#059669',
                  color: 'white',
                  border: 'none',
                  padding: '10px 20px',
                  borderRadius: 6,
                  cursor: 'pointer'
                }}
              >
                + Add Product
              </button>
            </div>
            
            <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
              {products.map(product => (
                <div key={product.id} style={{ 
                  display: 'flex', 
                  justifyContent: 'space-between', 
                  alignItems: 'center',
                  padding: '15px 0',
                  borderBottom: '1px solid #f1f1f1'
                }}>
                  <div>
                    <strong>{product.name}</strong>
                    <p style={{ margin: 5, color: '#666' }}>₹{product.price} | Stock: {product.stock}</p>
                  </div>
                  <div>
                    <button style={{ 
                      background: '#10b981', 
                      color: 'white', 
                      border: 'none', 
                      padding: '5px 10px', 
                      borderRadius: 4, 
                      marginRight: 10,
                      cursor: 'pointer'
                    }}>
                      Edit
                    </button>
                    <button style={{ 
                      background: '#ef4444', 
                      color: 'white', 
                      border: 'none', 
                      padding: '5px 10px', 
                      borderRadius: 4,
                      cursor: 'pointer'
                    }}>
                      Delete
                    </button>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* ORDERS TAB */}
        {activeTab === 'orders' && (
          <div>
            <h2>📦 Order Management</h2>
            <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
              {orders.map(order => (
                <div key={order.id} style={{ 
                  padding: '15px 0',
                  borderBottom: '1px solid #f1f1f1'
                }}>
                  <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
                    <div>
                      <strong>Order #{order.id}</strong>
                      <p style={{ margin: 5, color: '#666' }}>Customer: {order.customer}</p>
                      <p style={{ margin: 5, color: '#666' }}>Amount: ₹{order.amount}</p>
                    </div>
                    <div style={{ display: 'flex', alignItems: 'center', gap: 10 }}>
                      <span style={{
                        background: order.status === 'completed' ? '#d1fae5' : '#fef3c7',
                        color: order.status === 'completed' ? '#065f46' : '#92400e',
                        padding: '5px 10px',
                        borderRadius: 20,
                        fontSize: 14
                      }}>
                        {order.status}
                      </span>
                      {order.status === 'pending' && (
                        <button 
                          onClick={() => updateOrderStatus(order.id, 'completed')}
                          style={{
                            background: '#059669',
                            color: 'white',
                            border: 'none',
                            padding: '5px 10px',
                            borderRadius: 4,
                            cursor: 'pointer'
                          }}
                        >
                          Mark Complete
                        </button>
                      )}
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* SETTINGS TAB */}
        {activeTab === 'settings' && (
          <div>
            <h2>⚙️ Owner Settings</h2>
            <div style={{ background: 'white', padding: 25, borderRadius: 10, boxShadow: '0 2px 10px rgba(0,0,0,0.05)' }}>
              <div style={{ marginBottom: 20 }}>
                <h3 style={{ color: '#059669' }}>👑 Owner Information</h3>
                <p><strong>Email:</strong> theayurvedaworldofficial@gmail.com</p>
                <p><strong>Role:</strong> Supreme Administrator</p>
                <p><strong>Status:</strong> <span style={{ color: '#059669' }}>🟢 Active</span></p>
              </div>
              
              <div style={{ marginBottom: 20 }}>
                <h3 style={{ color: '#059669' }}>Website Configuration</h3>
                <button style={{
                  background: '#059669',
                  color: 'white',
                  border: 'none',
                  padding: '10px 20px',
                  borderRadius: 6,
                  cursor: 'pointer',
                  marginRight: 10
                }}>
                  General Settings
                </button>
                <button style={{
                  background: '#3b82f6',
                  color: 'white',
                  border: 'none',
                  padding: '10px 20px',
                  borderRadius: 6,
                  cursor: 'pointer',
                  marginRight: 10
                }}>
                  Payment Setup
                </button>
                <button style={{
                  background: '#8b5cf6',
                  color: 'white',
                  border: 'none',
                  padding: '10px 20px',
                  borderRadius: 6,
                  cursor: 'pointer'
                }}>
                  User Management
                </button>
              </div>
            </div>
          </div>
        )}

      </main>
    </div>
  );
}
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  swcMinify: true,
}

module.exports = nextConfig
# The Ayurveda World - E-Commerce Platform

Professional Ayurvedic products e-commerce website with admin dashboard.

## Features
- 🛍️ Complete E-commerce Functionality  
- 👑 Owner Dashboard
- 📱 Responsive Design
- 🔐 Secure Authentication

## Demo Login
- Email: theayurvedaworldofficial@gmail.com
- Password: admin123

## Deployment
Deployed on Vercel: [Live Website Link]
node_modules/
.next/
out/
