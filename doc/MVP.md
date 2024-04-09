# Розгортання MVP AsciiArtify за допомогою ArgoCD

## Вступ

AsciiArtify - це стартап, який розробляє програмний продукт для перетворення зображень у ascii-art за допомогою Machine Learning. Їх MVP (мінімально життєздатний продукт) буде розгорнуто за допомогою ArgoCD на Kubernetes кластері, створеному за допомогою minikube.

## Кроки

1. **Створення Git repository для MVP:**

   - Створіть Git repository для коду MVP: [https://github.com/den-vasyliev](https://github.com/den-vasyliev)

2. **Створення Helm chart для MVP:**

   - Створіть Helm chart для MVP, який буде використовуватися ArgoCD для розгортання.

3. **Додавання Helm repository ArgoCD:**

   - Додайте Helm repository ArgoCD:
     ```bash
     helm repo add argo https://argo-cd.github.io/argo-cd
     ```
   - Використовуйте цей код обачно.

4. **Створення ArgoCD Application:**

   - Створіть ArgoCD Application, який буде відслідковувати Git repository MVP та розгортати його на Kubernetes кластері:
     - В інтерфейсі ArgoCD перейдіть до "Applications" > "New".
     - Виберіть "Helm" як метод розгортання.
     - Вкажіть ім'я chart "ascii-artify-mvp".
     - Вкажіть URL-адресу Git repository MVP.
     - Вкажіть namespace "default".
     - Натисніть "Create".

5. **Тестування ArgoCD:**
   - Перевірте, чи успішно розгорнуто MVP:
     - В інтерфейсі ArgoCD перейдіть до "Applications".
     - Переконайтеся, що статус вашого Application "Synced".

## Демонстрація

Вбудоване демо: [https://github.com/den-vasyliev/go-demo-app](https://github.com/den-vasyliev/go-demo-app) демонструє, як ArgoCD автоматично відслідковує та синхронізує зміни з Git repository MVP та розгортає їх на Kubernetes кластері.

## Висновок

ArgoCD - це потужний інструмент, який можна використовувати для автоматизації розгортання MVP AsciiArtify. Цей PoC продемонстрував, як ArgoCD можна використовувати для відстеження Git repository MVP та розгортання його на Kubernetes кластері.
