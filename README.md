import React, { useState, useEffect } from 'react';
import { Mail, FileText, Github, Linkedin, Instagram, Youtube, Code, Award, Star, Eye, Users, Calendar, ChevronDown, Rocket, Brain, Database, Globe, Zap, Cloud, GitBranch, MonitorSpeaker, Settings, Cpu } from 'lucide-react';

const App = () => {
  const [profileViews, setProfileViews] = useState(0);
  const [followers, setFollowers] = useState(0);
  const [stars, setStars] = useState(0);
  const [currentText, setCurrentText] = useState('');
  const [textIndex, setTextIndex] = useState(0);
  
  const expertiseAreas = [
    'Data Science Expert',
    'ML Engineering',
    'AI Development',
    'Algorithm Design',
    'Web Development'
  ];

  // Animated counter effect
  useEffect(() => {
    const animateCounter = (setter, target, duration = 2000) => {
      let start = 0;
      const increment = target / (duration / 16);
      const timer = setInterval(() => {
        start += increment;
        if (start >= target) {
          start = target;
          clearInterval(timer);
        }
        setter(Math.floor(start));
      }, 16);
    };

    setTimeout(() => {
      animateCounter(setProfileViews, 1247);
      animateCounter(setFollowers, 86);
      animateCounter(setStars, 152);
    }, 500);
  }, []);

  // Typewriter effect
  useEffect(() => {
    const text = expertiseAreas[textIndex];
    let charIndex = 0;
    
    const typeWriter = () => {
      if (charIndex < text.length) {
        setCurrentText(text.slice(0, charIndex + 1));
        charIndex++;
        setTimeout(typeWriter, 100);
      } else {
        setTimeout(() => {
          setTextIndex((prev) => (prev + 1) % expertiseAreas.length);
          setCurrentText('');
        }, 2000);
      }
    };

    const timeout = setTimeout(typeWriter, 500);
    return () => clearTimeout(timeout);
  }, [textIndex]);

  const skills = [
    { name: 'Python', level: 90, icon: <Code className="w-6 h-6" />, color: 'from-blue-500 to-blue-600' },
    { name: 'Machine Learning', level: 85, icon: <Brain className="w-6 h-6" />, color: 'from-blue-600 to-indigo-600' },
    { name: 'Data Science', level: 88, icon: <Database className="w-6 h-6" />, color: 'from-cyan-500 to-blue-500' },
    { name: 'AWS', level: 75, icon: <Cloud className="w-6 h-6" />, color: 'from-sky-500 to-blue-600' },
    { name: 'Web Development', level: 80, icon: <Globe className="w-6 h-6" />, color: 'from-indigo-500 to-blue-600' },
    { name: 'Git/GitHub', level: 85, icon: <GitBranch className="w-6 h-6" />, color: 'from-slate-500 to-blue-600' }
  ];

  const projects = [
    { name: 'AI Research', description: 'Advanced ML algorithms', color: 'from-blue-500 to-indigo-600' },
    { name: 'Data Analytics', description: 'Big data processing', color: 'from-cyan-500 to-blue-600' },
    { name: 'Web Apps', description: 'Full-stack development', color: 'from-sky-500 to-blue-600' },
    { name: 'Automation', description: 'Process optimization', color: 'from-indigo-500 to-blue-700' }
  ];

  const socialLinks = [
    { name: 'LinkedIn', url: 'https://linkedin.com/in/r06', icon: <Linkedin className="w-6 h-6" />, color: 'hover:bg-blue-100 hover:text-blue-700' },
    { name: 'GitHub', url: 'https://github.com/rudr19', icon: <Github className="w-6 h-6" />, color: 'hover:bg-gray-100 hover:text-gray-700' },
    { name: 'Kaggle', url: 'https://kaggle.com/rudrakumarpandey', icon: <Award className="w-6 h-6" />, color: 'hover:bg-cyan-100 hover:text-cyan-700' },
    { name: 'Instagram', url: 'https://www.instagram.com/rudr1_20', icon: <Instagram className="w-6 h-6" />, color: 'hover:bg-pink-100 hover:text-pink-700' },
    { name: 'YouTube', url: 'https://www.youtube.com/@Redbloodtales.', icon: <Youtube className="w-6 h-6" />, color: 'hover:bg-red-100 hover:text-red-700' },
    { name: 'LeetCode', url: 'https://www.leetcode.com/r06', icon: <Code className="w-6 h-6" />, color: 'hover:bg-yellow-100 hover:text-yellow-700' }
  ];

  const Particle = ({ delay = 0 }) => (
    <div
      className="absolute w-1 h-1 bg-blue-300 rounded-full opacity-60 animate-pulse"
      style={{
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${delay}s`,
        animationDuration: `${2 + Math.random() * 3}s`
      }}
    />
  );

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-50 via-white to-blue-100 text-gray-800 overflow-hidden">
      {/* Animated Background */}
      <div className="fixed inset-0 overflow-hidden pointer-events-none">
        {[...Array(50)].map((_, i) => (
          <Particle key={i} delay={i * 0.1} />
        ))}
      </div>

      {/* Hero Section */}
      <section className="relative min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8">
        <div className="text-center z-10 max-w-5xl mx-auto">
          {/* Profile Avatar */}
          <div className="relative mb-8 inline-block">
            <div className="w-32 h-32 sm:w-40 sm:h-40 bg-gradient-to-r from-blue-500 via-indigo-500 to-blue-600 rounded-full flex items-center justify-center text-4xl sm:text-5xl font-bold text-white shadow-2xl animate-pulse">
              RK
            </div>
            <div className="absolute inset-0 rounded-full bg-gradient-to-r from-blue-400 via-indigo-400 to-blue-500 blur-xl opacity-30 animate-ping"></div>
          </div>

          {/* Main Title */}
          <h1 className="text-4xl sm:text-6xl lg:text-7xl font-bold mb-6 bg-gradient-to-r from-blue-600 via-indigo-600 to-blue-700 bg-clip-text text-transparent">
            Hi <span className="inline-block animate-bounce">👋</span>, I'm Rudra Kumar Pandey
          </h1>

          {/* Typewriter Effect */}
          <div className="text-xl sm:text-2xl lg:text-3xl mb-8 h-12 flex items-center justify-center">
            <span className="text-gray-600">A passionate </span>
            <span className="ml-2 text-blue-600 font-semibold min-w-64 text-left">
              {currentText}
              <span className="animate-pulse">|</span>
            </span>
          </div>

          {/* Stats */}
          <div className="grid grid-cols-1 sm:grid-cols-3 gap-6 mb-12 max-w-2xl mx-auto">
            {[
              { label: 'Profile Views', value: profileViews, icon: <Eye className="w-6 h-6" /> },
              { label: 'Followers', value: followers, icon: <Users className="w-6 h-6" /> },
              { label: 'Stars', value: stars, icon: <Star className="w-6 h-6" /> }
            ].map((stat, index) => (
              <div
                key={stat.label}
                className="bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-6 hover:scale-105 transition-all duration-300 hover:bg-white hover:shadow-xl shadow-lg"
                style={{ animationDelay: `${index * 0.2}s` }}
              >
                <div className="flex items-center justify-center mb-2 text-blue-600">
                  {stat.icon}
                </div>
                <div className="text-2xl font-bold text-gray-800">{stat.value.toLocaleString()}</div>
                <div className="text-gray-600 text-sm">{stat.label}</div>
              </div>
            ))}
          </div>

          {/* Scroll Indicator */}
          <div className="animate-bounce">
            <ChevronDown className="w-8 h-8 mx-auto text-blue-500" />
          </div>
        </div>
      </section>

      {/* Current Work Section */}
      <section className="py-20 px-4 sm:px-6 lg:px-8 relative">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-3xl sm:text-4xl font-bold mb-4 bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
              🌱 Currently Working On
            </h2>
            <p className="text-gray-600 text-lg">Exploring cutting-edge technologies and building innovative solutions</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            {projects.map((project, index) => (
              <div
                key={project.name}
                className="group relative bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-6 hover:scale-105 transition-all duration-500 hover:bg-white hover:shadow-xl shadow-lg"
                style={{ animationDelay: `${index * 0.1}s` }}
              >
                <div className={`absolute inset-0 bg-gradient-to-r ${project.color} opacity-0 group-hover:opacity-10 rounded-2xl transition-opacity duration-500`}></div>
                <div className="relative z-10">
                  <div className="text-4xl mb-4">
                    {index === 0 && <Rocket className="w-8 h-8 text-blue-600" />}
                    {index === 1 && <Database className="w-8 h-8 text-cyan-600" />}
                    {index === 2 && <Globe className="w-8 h-8 text-indigo-600" />}
                    {index === 3 && <Zap className="w-8 h-8 text-blue-700" />}
                  </div>
                  <h3 className="text-xl font-semibold mb-2 text-gray-800">{project.name}</h3>
                  <p className="text-gray-600">{project.description}</p>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Skills Section */}
      <section className="py-20 px-4 sm:px-6 lg:px-8 bg-blue-50/50">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-3xl sm:text-4xl font-bold mb-4 bg-gradient-to-r from-indigo-600 to-blue-600 bg-clip-text text-transparent">
              🛠️ Skills & Expertise
            </h2>
            <p className="text-gray-600 text-lg">Technologies I work with and master continuously</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {skills.map((skill, index) => (
              <div
                key={skill.name}
                className="bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-6 hover:scale-105 transition-all duration-300 group hover:shadow-xl shadow-lg"
                style={{ animationDelay: `${index * 0.1}s` }}
              >
                <div className="flex items-center mb-4">
                  <div className={`p-3 rounded-xl bg-gradient-to-r ${skill.color} mr-4 group-hover:scale-110 transition-transform duration-300 text-white`}>
                    {skill.icon}
                  </div>
                  <div>
                    <h3 className="font-semibold text-lg text-gray-800">{skill.name}</h3>
                    <p className="text-gray-600 text-sm">{skill.level}% Proficiency</p>
                  </div>
                </div>
                <div className="w-full bg-blue-100 rounded-full h-2 overflow-hidden">
                  <div
                    className={`h-full bg-gradient-to-r ${skill.color} rounded-full transition-all duration-1000 ease-out`}
                    style={{ width: `${skill.level}%` }}
                  ></div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section className="py-20 px-4 sm:px-6 lg:px-8">
        <div className="max-w-4xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-3xl sm:text-4xl font-bold mb-4 bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
              📫 Get In Touch
            </h2>
            <p className="text-gray-600 text-lg">Let's connect and collaborate on amazing projects</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12">
            <a
              href="mailto:rudrakumarpandey47@gmail.com"
              className="group bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-8 hover:scale-105 transition-all duration-300 hover:bg-white hover:shadow-xl shadow-lg"
            >
              <div className="flex items-center">
                <div className="p-4 bg-gradient-to-r from-blue-500 to-indigo-600 rounded-xl mr-6 group-hover:scale-110 transition-transform duration-300 text-white">
                  <Mail className="w-8 h-8" />
                </div>
                <div>
                  <h3 className="text-xl font-semibold mb-2 text-gray-800">Email Me</h3>
                  <p className="text-gray-600">rudrakumarpandey47@gmail.com</p>
                </div>
              </div>
            </a>

            <a
              href="https://drive.google.com/file/d/1ph4eZqXuMs74wQ_i6UCeYbR9XFHuDLxq/view"
              target="_blank"
              rel="noopener noreferrer"
              className="group bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-8 hover:scale-105 transition-all duration-300 hover:bg-white hover:shadow-xl shadow-lg"
            >
              <div className="flex items-center">
                <div className="p-4 bg-gradient-to-r from-cyan-500 to-blue-600 rounded-xl mr-6 group-hover:scale-110 transition-transform duration-300 text-white">
                  <FileText className="w-8 h-8" />
                </div>
                <div>
                  <h3 className="text-xl font-semibold mb-2 text-gray-800">View Resume</h3>
                  <p className="text-gray-600">Download my latest CV</p>
                </div>
              </div>
            </a>
          </div>

          {/* Social Links */}
          <div className="text-center">
            <h3 className="text-2xl font-semibold mb-8 text-gray-700">🌐 Connect With Me</h3>
            <div className="flex flex-wrap justify-center gap-4">
              {socialLinks.map((social, index) => (
                <a
                  key={social.name}
                  href={social.url}
                  target="_blank"
                  rel="noopener noreferrer"
                  className={`group p-4 bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl transition-all duration-300 hover:scale-110 shadow-lg hover:shadow-xl ${social.color}`}
                  style={{ animationDelay: `${index * 0.1}s` }}
                >
                  <div className="flex items-center justify-center w-12 h-12 text-gray-700">
                    {social.icon}
                  </div>
                  <span className="sr-only">{social.name}</span>
                </a>
              ))}
            </div>
          </div>
        </div>
      </section>

      {/* GitHub Stats */}
      <section className="py-20 px-4 sm:px-6 lg:px-8 bg-blue-50/50">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-3xl sm:text-4xl font-bold mb-4 bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
              📊 GitHub Analytics
            </h2>
            <p className="text-gray-600 text-lg">My coding journey and contributions</p>
          </div>

          <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
            <div className="bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-8 hover:scale-105 transition-all duration-300 shadow-lg hover:shadow-xl">
              <h3 className="text-xl font-semibold mb-4 text-center text-gray-800">Most Used Languages</h3>
              <img
                src="https://github-readme-stats.vercel.app/api/top-langs?username=rudr19&show_icons=true&locale=en&layout=compact&theme=default"
                alt="Top Languages"
                className="w-full rounded-lg"
                loading="lazy"
              />
            </div>

            <div className="bg-white/80 backdrop-blur-lg border border-blue-200 rounded-2xl p-8 hover:scale-105 transition-all duration-300 shadow-lg hover:shadow-xl">
              <h3 className="text-xl font-semibold mb-4 text-center text-gray-800">Coding Streak</h3>
              <img
                src="https://github-readme-streak-stats.herokuapp.com/?user=rudr19&theme=default"
                alt="GitHub Streak"
                className="w-full rounded-lg"
                loading="lazy"
              />
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="py-12 px-4 sm:px-6 lg:px-8 border-t border-blue-200 bg-white/50">
        <div className="max-w-6xl mx-auto text-center">
          <p className="text-gray-600 mb-4">
            Made with ❤️ by Rudra Kumar Pandey
          </p>
          <p className="text-gray-500 text-sm">
            © 2024 All rights reserved. Crafted with passion for innovation.
          </p>
        </div>
      </footer>
    </div>
  );
};

export default App;
