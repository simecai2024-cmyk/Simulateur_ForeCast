<template>
  <div class="page">
    <header class="hero">
      <p class="badge">Simulateur ForeCast</p>
      <h1>Interfaces de connexion conviviales</h1>
      <p>
        Choisissez un scénario pour visualiser les écrans de connexion, d'accès accepté ou
        d'accès refusé.
      </p>
      <div class="toggle">
        <button
          :class="{ active: activeView === 'login' }"
          @click="activeView = 'login'"
        >
          Connexion
        </button>
        <button
          :class="{ active: activeView === 'accept' }"
          @click="activeView = 'accept'"
        >
          Accès accepté
        </button>
        <button
          :class="{ active: activeView === 'refuse' }"
          @click="activeView = 'refuse'"
        >
          Accès refusé
        </button>
      </div>
    </header>

    <main class="cards">
      <section v-if="activeView === 'login'" class="card">
        <div class="card-header">
          <span class="icon">🔐</span>
          <div>
            <h2>Connexion sécurisée</h2>
            <p>Accédez à votre espace en toute simplicité.</p>
          </div>
        </div>
        <form class="form" @submit.prevent>
          <label>
            Adresse e-mail
            <input type="email" placeholder="vous@exemple.com" required />
          </label>
          <label>
            Mot de passe
            <input type="password" placeholder="••••••••" required />
          </label>
          <div class="form-actions">
            <button type="submit">Se connecter</button>
            <button type="button" class="ghost">Mot de passe oublié</button>
          </div>
        </form>
      </section>

      <section v-if="activeView === 'accept'" class="card success">
        <div class="card-header">
          <span class="icon">✅</span>
          <div>
            <h2>Accès accepté</h2>
            <p>Bienvenue ! Votre connexion a été validée.</p>
          </div>
        </div>
        <ul class="status-list">
          <li>
            <strong>Statut :</strong>
            <span class="pill">Connexion confirmée</span>
          </li>
          <li>
            <strong>Dernière vérification :</strong>
            <span>Il y a 2 minutes</span>
          </li>
          <li>
            <strong>Conseil :</strong>
            <span>Activez la double authentification pour plus de sécurité.</span>
          </li>
        </ul>
        <button class="primary">Accéder au tableau de bord</button>
      </section>

      <section v-if="activeView === 'refuse'" class="card danger">
        <div class="card-header">
          <span class="icon">⛔️</span>
          <div>
            <h2>Accès refusé</h2>
            <p>Nous n'avons pas pu confirmer votre identité.</p>
          </div>
        </div>
        <div class="alert">
          <p>
            Vérifiez vos identifiants ou utilisez l'assistance pour réinitialiser votre mot
            de passe.
          </p>
        </div>
        <div class="form-actions">
          <button class="primary" @click="activeView = 'login'">Réessayer</button>
          <button class="ghost" type="button">Contacter le support</button>
        </div>
      </section>
    </main>

    <footer class="footer">
      <p>Ces interfaces illustrent les différents états de connexion pour un parcours fluide.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from "vue";

const activeView = ref("login");
</script>

<style scoped>
:global(body) {
  margin: 0;
  font-family: "Inter", "Segoe UI", system-ui, sans-serif;
  background: #f5f7fb;
  color: #1a1c2d;
}

.page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  gap: 32px;
  padding: 40px 24px 32px;
}

.hero {
  max-width: 960px;
  margin: 0 auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.badge {
  align-self: center;
  padding: 6px 14px;
  background: #eef1ff;
  color: #3f51ff;
  border-radius: 999px;
  font-weight: 600;
  font-size: 0.85rem;
}

.toggle {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 12px;
  margin-top: 8px;
}

.toggle button {
  border: 1px solid transparent;
  background: #ffffff;
  padding: 10px 18px;
  border-radius: 999px;
  cursor: pointer;
  font-weight: 600;
  color: #3b3f5a;
  box-shadow: 0 8px 16px rgba(15, 23, 42, 0.08);
  transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
}

.toggle button:hover {
  transform: translateY(-1px);
  box-shadow: 0 12px 24px rgba(15, 23, 42, 0.12);
}

.toggle button.active {
  border-color: #3f51ff;
  color: #3f51ff;
}

.cards {
  max-width: 960px;
  margin: 0 auto;
  width: 100%;
}

.card {
  background: #ffffff;
  border-radius: 24px;
  padding: 28px;
  box-shadow: 0 20px 40px rgba(15, 23, 42, 0.12);
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.card.success {
  border: 1px solid #d1f4df;
  background: linear-gradient(140deg, #ffffff 0%, #f0fffa 100%);
}

.card.danger {
  border: 1px solid #ffd4d4;
  background: linear-gradient(140deg, #ffffff 0%, #fff4f4 100%);
}

.card-header {
  display: flex;
  align-items: center;
  gap: 16px;
}

.icon {
  font-size: 2.2rem;
}

.form {
  display: grid;
  gap: 16px;
}

.form label {
  display: grid;
  gap: 8px;
  font-weight: 600;
  color: #3b3f5a;
}

.form input {
  padding: 12px 14px;
  border-radius: 12px;
  border: 1px solid #e2e8f0;
  font-size: 1rem;
}

.form-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

button {
  border: none;
  padding: 12px 18px;
  border-radius: 12px;
  font-weight: 600;
  cursor: pointer;
}

button.primary {
  background: #3f51ff;
  color: #ffffff;
}

button.ghost {
  background: #eef1ff;
  color: #3f51ff;
}

.status-list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  gap: 12px;
}

.status-list li {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
}

.pill {
  background: #d1f4df;
  color: #147a3d;
  padding: 4px 10px;
  border-radius: 999px;
  font-size: 0.85rem;
}

.alert {
  background: #fff0f0;
  border-radius: 16px;
  padding: 16px;
  color: #b42318;
}

.footer {
  text-align: center;
  color: #6b7280;
}

@media (max-width: 720px) {
  .card {
    padding: 22px;
  }

  .form-actions {
    flex-direction: column;
  }
}
</style>
