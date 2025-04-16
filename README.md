import { Button } from "@/components/ui/button"; import { motion, AnimatePresence } from "framer-motion"; import { ArrowRight, Menu, X } from "lucide-react"; import { useEffect, useState } from "react";

export default function Home() { useEffect(() => { document.documentElement.classList.add("dark"); }, []);

const [menuOpen, setMenuOpen] = useState(false); const [loading, setLoading] = useState(true);

useEffect(() => { const timer = setTimeout(() => setLoading(false), 2000); return () => clearTimeout(timer); }, []);

const handleSubmit = (e) => { e.preventDefault(); e.target.reset(); alert("Сообщение отправлено!"); };

if (loading) { return ( <div className="min-h-screen bg-black flex items-center justify-center"> <motion.div initial={{ scale: 0 }} animate={{ scale: 1 }} transition={{ duration: 0.5, repeat: Infinity, repeatType: "reverse" }} className="w-12 h-12 rounded-full bg-gradient-to-r from-purple-500 to-pink-500 shadow-lg" /> </div> ); }

return ( <div className="min-h-screen bg-gradient-to-br from-[#0f0f0f] to-[#1a1a1a] text-white scroll-smooth"> {/* Header */} <header className="p-4 md:p-6 flex justify-between items-center max-w-6xl mx-auto"> <h1 className="text-2xl font-bold">TelegaPro</h1> <div className="md:hidden"> <button onClick={() => setMenuOpen(!menuOpen)}> {menuOpen ? <X size={28} /> : <Menu size={28} />} </button> </div> <nav className="hidden md:flex space-x-4"> <a href="#about" className="hover:underline">О нас</a> <a href="#features" className="hover:underline">Преимущества</a> <a href="#contact" className="hover:underline">Контакты</a> </nav> </header>

{/* Mobile Menu */}
  <AnimatePresence>
    {menuOpen && (
      <motion.nav
        initial={{ height: 0, opacity: 0 }}
        animate={{ height: "auto", opacity: 1 }}
        exit={{ height: 0, opacity: 0 }}
        className="md:hidden flex flex-col items-center space-y-4 pb-6"
      >
        <a href="#about" onClick={() => setMenuOpen(false)}>О нас</a>
        <a href="#features" onClick={() => setMenuOpen(false)}>Преимущества</a>
        <a href="#contact" onClick={() => setMenuOpen(false)}>Контакты</a>
      </motion.nav>
    )}
  </AnimatePresence>

  {/* Hero Section */}
  <section className="flex flex-col items-center justify-center text-center px-4 py-16 sm:py-20">
    <motion.h2 
      initial={{ opacity: 0, y: 20 }} 
      animate={{ opacity: 1, y: 0 }} 
      transition={{ duration: 0.6 }}
      className="text-3xl sm:text-4xl md:text-5xl font-extrabold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-500">
      Продвигайся в Telegram качественно
    </motion.h2>
    <motion.p 
      initial={{ opacity: 0 }} 
      animate={{ opacity: 1 }} 
      transition={{ delay: 0.3 }}
      className="text-base sm:text-lg mb-8 max-w-2xl">
      Наша команда поможет тебе набрать живую и активную аудиторию в Telegram быстро и безопасно.
    </motion.p>
    <motion.div
      initial={{ opacity: 0, scale: 0.95 }}
      animate={{ opacity: 1, scale: 1 }}
      transition={{ delay: 0.6 }}
    >
      <Button size="lg" className="text-base gap-2">
        Связаться в Telegram <ArrowRight size={18} />
      </Button>
    </motion.div>
  </section>

  {/* Features Section */}
  <section id="features" className="bg-[#121212] py-16 px-4 sm:px-6">
    <div className="max-w-5xl mx-auto grid sm:grid-cols-2 md:grid-cols-3 gap-6 sm:gap-8 text-center">
      {[
        {
          title: "Безопасность",
          desc: "Никаких блокировок и теневых банов."
        },
        {
          title: "Реальные пользователи",
          desc: "Продвижение только через живую аудиторию."
        },
        {
          title: "Быстрый старт",
          desc: "Запуск в течение 24 часов после заявки."
        },
      ].map((feature, i) => (
        <motion.div 
          key={i} 
          initial={{ opacity: 0, y: 40 }} 
          whileInView={{ opacity: 1, y: 0 }} 
          transition={{ delay: i * 0.2, duration: 0.5 }}
          viewport={{ once: true }}
          className="bg-[#1f1f1f] p-6 rounded-2xl shadow-lg">
          <h3 className="text-lg sm:text-xl font-semibold mb-2">{feature.title}</h3>
          <p className="text-sm text-gray-300">{feature.desc}</p>
        </motion.div>
      ))}
    </div>
  </section>

  {/* Contact Section */}
  <section id="contact" className="text-center py-20 px-4">
    <motion.h2 
      initial={{ opacity: 0, y: 10 }} 
      whileInView={{ opacity: 1, y: 0 }} 
      viewport={{ once: true }}
      transition={{ duration: 0.5 }}
      className="text-2xl sm:text-3xl font-bold mb-4">
      Остались вопросы?
    </motion.h2>
    <motion.p
      initial={{ opacity: 0 }}
      whileInView={{ opacity: 1 }}
      viewport={{ once: true }}
      transition={{ delay: 0.2 }}
      className="mb-6 text-base sm:text-lg">
      Напиши нам — поможем, проконсультируем и подберём лучший вариант.
    </motion.p>
    <motion.div
      initial={{ opacity: 0, scale: 0.95 }}
      whileInView={{ opacity: 1, scale: 1 }}
      viewport={{ once: true }}
      transition={{ delay: 0.4 }}
    >
      <Button size="lg" className="gap-2">
        Написать в Telegram <ArrowRight size={18} />
      </Button>
    </motion.div>
  </section>

  {/* Contact Form */}
  <section className="py-20 bg-[#1b1b1b] px-4">
    <div className="max-w-xl mx-auto">
      <motion.h3
        initial={{ opacity: 0, y: 10 }}
        whileInView={{ opacity: 1, y: 0 }}
        viewport={{ once: true }}
        transition={{ duration: 0.5 }}
        className="text-xl sm:text-2xl font-bold mb-4 text-center">
        Форма обратной связи
      </motion.h3>
      <motion.form 
        initial={{ opacity: 0 }} 
        whileInView={{ opacity: 1 }} 
        viewport={{ once: true }}
        transition={{ delay: 0.2 }}
        className="space-y-4" 
        onSubmit={handleSubmit}>
        <input
          type="text"
          name="name"
          placeholder="Ваше имя"
          className="w-full px-4 py-2 rounded-lg bg-[#2a2a2a] text-white placeholder-gray-400 focus:outline-none"
          required
        />
        <input
          type="text"
          name="contact"
          placeholder="Email или Telegram"
          className="w-full px-4 py-2 rounded-lg bg-[#2a2a2a] text-white placeholder-gray-400 focus:outline-none"
          required
        />
        <textarea
          name="message"
          placeholder="Ваше сообщение"
          rows="4"
          className="w-full px-4 py-2 rounded-lg bg-[#2a2a2a] text-white placeholder-gray-400 focus:outline-none"
          required
        />
        <Button type="submit" className="w-full">Отправить</Button>
      </motion.form>
    </div>
  </section>

  <footer className="text-center py-6 text-sm text-gray-500 px-4">
    © {new Date().getFullYear()} TelegaPro. Все права защищены.
  </footer>
</div>

); }

