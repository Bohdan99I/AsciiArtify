# Proof of Concept (PoC) GitOps-системи ArgoCD на Kubernetes для AsciiArtify

## Кроки

### Створення Kubernetes кластеру:

1. Завантажте та встановіть minikube: [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)
2. Запустіть minikube кластер:
   ```bash
   minikube start
   ```

### Встановлення ArgoCD:

3. Додайте Helm repository ArgoCD:

   ```bash
   helm repo add argo https://argo-cd.github.io/argo-helm
   ```

4. Встановіть ArgoCD Helm chart:

   ```bash
   helm install argo-cd argo/argo-cd --namespace argo
   ```

5. Налаштуйте ArgoCD API Server:

   ```bash
   kubectl port-forward deployment/argo-cd -n argo 8080:8080
   ```

6. Отримайте доступ до інтерфейсу ArgoCD: [https://localhost:8080/](https://localhost:8080/)

### Тестування ArgoCD:

7. Створіть Git repository для коду AsciiArtify.
8. Підключіть Git repository до ArgoCD:
   - В інтерфейсі ArgoCD перейдіть до "Repositories" > "New".
   - Вкажіть URL-адресу вашого Git repository.
   - Натисніть "Sync".
9. Створіть ArgoCD Application для розгортання коду AsciiArtify:
   - В інтерфейсі ArgoCD перейдіть до "Applications" > "New".
   - Виберіть "Helm" як метод розгортання.
   - Вкажіть ім'я chart "argo-cd".
   - Вкажіть namespace "default".
   - Натисніть "Create".
10. Перевірте, чи успішно розгорнуто код AsciiArtify:
    - В інтерфейсі ArgoCD перейдіть до "Applications".
    - Переконайтеся, що статус вашого Application "Synced".

## Демонстрація

[https://m.youtube.com/watch?v=0WAm0y2vLIo](https://m.youtube.com/watch?v=0WAm0y2vLIo) - це офіційна демонстрація ArgoCD, яка показує основні можливості системи.

## Висновок

ArgoCD - це потужна GitOps-система, яка може допомогти AsciiArtify автоматизувати розгортання свого продукту. Цей PoC продемонстрував, що ArgoCD можна легко розгорнути на Kubernetes кластері та використовувати для автоматичного розгортання коду AsciiArtify.
