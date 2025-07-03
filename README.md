
# Django Notes App

## Overview

Django Notes App is a full-stack web application for managing personal notes, featuring a RESTful API backend built with Django and a responsive React frontend. The project is containerized with Docker and deployed on Kubernetes using Helm charts with auto-scaling capabilities powered by the Horizontal Pod Autoscaler (HPA).

---

## Features

- Create, read, update, and delete notes via REST API  
- Interactive React frontend with intuitive UI  
- Kubernetes deployment with Helm charts for easy scaling and management  
- Auto-scaling based on CPU utilization with HPA  
- CI/CD pipeline configured using Jenkins for automated builds and deployments

---

## Tech Stack

- **Backend:** Django, Django REST Framework  
- **Frontend:** React.js  
- **Containerization:** Docker  
- **Orchestration:** Kubernetes, Helm  
- **CI/CD:** Jenkins  
- **Monitoring:** Kubernetes Metrics Server (required for HPA)  

---

## Project Structure

```
.
└── django-notes-app
    ├── api
    │   ├── __init__.py
    │   ├── __pycache__
    │   │   ├── __init__.cpython-311.pyc
    │   │   ├── admin.cpython-311.pyc
    │   │   ├── apps.cpython-311.pyc
    │   │   ├── models.cpython-311.pyc
    │   │   ├── serializers.cpython-311.pyc
    │   │   ├── urls.cpython-311.pyc
    │   │   └── views.cpython-311.pyc
    │   ├── admin.py
    │   ├── apps.py
    │   ├── migrations
    │   │   ├── __init__.py
    │   │   ├── __pycache__
    │   │   │   ├── __init__.cpython-311.pyc
    │   │   │   └── 0001_initial.cpython-311.pyc
    │   │   └── 0001_initial.py
    │   ├── models.py
    │   ├── serializers.py
    │   ├── tests.py
    │   ├── urls.py
    │   └── views.py
    ├── db.sqlite3
    ├── docker-compose.yml
    ├── Dockerfile
    ├── Jenkinsfile
    ├── k8s
    │   ├── deployment.yml
    │   ├── namespace.yml
    │   └── service.yml
    ├── manage.py
    ├── mynotes
    │   ├── build
    │   │   ├── asset-manifest.json
    │   │   ├── favicon.ico
    │   │   ├── index.html
    │   │   ├── logo192.png
    │   │   ├── logo512.png
    │   │   ├── manifest.json
    │   │   ├── robots.txt
    │   │   └── static
    │   │       ├── css
    │   │       │   ├── main.e7772a38.css
    │   │       │   └── main.e7772a38.css.map
    │   │       ├── js
    │   │       │   ├── main.08442c14.js
    │   │       │   ├── main.08442c14.js.LICENSE.txt
    │   │       │   └── main.08442c14.js.map
    │   │       └── media
    │   │           ├── add.ebf598626c6f9b2211b0578a435aaa6b.svg
    │   │           └── arrow-left.b553318e4fdaed1113efb091889b7f47.svg
    │   ├── db.json
    │   ├── Dockerfile
    │   ├── package-lock.json
    │   ├── package.json
    │   ├── public
    │   │   ├── favicon.ico
    │   │   ├── index.html
    │   │   ├── logo192.png
    │   │   ├── logo512.png
    │   │   ├── manifest.json
    │   │   └── robots.txt
    │   └── src
    │       ├── App.css
    │       ├── App.js
    │       ├── assets
    │       │   ├── add.svg
    │       │   ├── arrow-left.svg
    │       │   ├── data.js
    │       │   └── db.json
    │       ├── components
    │       │   ├── AddButton.js
    │       │   ├── header.js
    │       │   └── ListItem.js
    │       ├── index.js
    │       └── pages
    │           ├── NotePage.js
    │           └── NotesListPage.js
    ├── notesapp
    │   ├── __init__.py
    │   ├── __pycache__
    │   │   ├── __init__.cpython-311.pyc
    │   │   ├── settings.cpython-311.pyc
    │   │   ├── urls.cpython-311.pyc
    │   │   └── wsgi.cpython-311.pyc
    │   ├── asgi.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── notesappchart
    │   ├── Chart.yaml
    │   ├── charts
    │   ├── templates
    │   │   ├── _helpers.tpl
    │   │   ├── deployment.yaml
    │   │   ├── hpa.yaml
    │   │   ├── ingress.yaml
    │   │   ├── NOTES.txt
    │   │   ├── service.yaml
    │   │   ├── serviceaccount.yaml
    │   │   └── tests
    │   │       └── test-connection.yaml
    │   └── values.yaml
    ├── procfile
    ├── README.md
    ├── requirements.txt
    └── staticfiles
        ├── admin
        │   ├── css
        │   │   ├── autocomplete.css
        │   │   ├── base.css
        │   │   ├── changelists.css
        │   │   ├── dark_mode.css
        │   │   ├── dashboard.css
        │   │   ├── fonts.css
        │   │   ├── forms.css
        │   │   ├── login.css
        │   │   ├── nav_sidebar.css
        │   │   ├── responsive_rtl.css
        │   │   ├── responsive.css
        │   │   ├── rtl.css
        │   │   ├── vendor
        │   │   │   └── select2
        │   │   │       ├── LICENSE-SELECT2.md
        │   │   │       ├── select2.css
        │   │   │       └── select2.min.css
        │   │   └── widgets.css
        │   ├── fonts
        │   │   ├── LICENSE.txt
        │   │   ├── README.txt
        │   │   ├── Roboto-Bold-webfont.woff
        │   │   ├── Roboto-Light-webfont.woff
        │   │   └── Roboto-Regular-webfont.woff
        │   ├── img
        │   │   ├── calendar-icons.svg
        │   │   ├── gis
        │   │   │   ├── move_vertex_off.svg
        │   │   │   └── move_vertex_on.svg
        │   │   ├── icon-addlink.svg
        │   │   ├── icon-alert.svg
        │   │   ├── icon-calendar.svg
        │   │   ├── icon-changelink.svg
        │   │   ├── icon-clock.svg
        │   │   ├── icon-deletelink.svg
        │   │   ├── icon-no.svg
        │   │   ├── icon-unknown-alt.svg
        │   │   ├── icon-unknown.svg
        │   │   ├── icon-viewlink.svg
        │   │   ├── icon-yes.svg
        │   │   ├── inline-delete.svg
        │   │   ├── LICENSE
        │   │   ├── README.txt
        │   │   ├── search.svg
        │   │   ├── selector-icons.svg
        │   │   ├── sorting-icons.svg
        │   │   ├── tooltag-add.svg
        │   │   └── tooltag-arrowright.svg
        │   └── js
        │       ├── actions.js
        │       ├── admin
        │       │   ├── DateTimeShortcuts.js
        │       │   └── RelatedObjectLookups.js
        │       ├── autocomplete.js
        │       ├── calendar.js
        │       ├── cancel.js
        │       ├── change_form.js
        │       ├── collapse.js
        │       ├── core.js
        │       ├── filters.js
        │       ├── inlines.js
        │       ├── jquery.init.js
        │       ├── nav_sidebar.js
        │       ├── popup_response.js
        │       ├── prepopulate_init.js
        │       ├── prepopulate.js
        │       ├── SelectBox.js
        │       ├── SelectFilter2.js
        │       ├── urlify.js
        │       └── vendor
        │           ├── jquery
        │           │   ├── jquery.js
        │           │   ├── jquery.min.js
        │           │   └── LICENSE.txt
        │           ├── select2
        │           │   ├── i18n
        │           │   │   ├── af.js
        │           │   │   ├── ar.js
        │           │   │   ├── az.js
        │           │   │   ├── bg.js
        │           │   │   ├── bn.js
        │           │   │   ├── bs.js
        │           │   │   ├── ca.js
        │           │   │   ├── cs.js
        │           │   │   ├── da.js
        │           │   │   ├── de.js
        │           │   │   ├── dsb.js
        │           │   │   ├── el.js
        │           │   │   ├── en.js
        │           │   │   ├── es.js
        │           │   │   ├── et.js
        │           │   │   ├── eu.js
        │           │   │   ├── fa.js
        │           │   │   ├── fi.js
        │           │   │   ├── fr.js
        │           │   │   ├── gl.js
        │           │   │   ├── he.js
        │           │   │   ├── hi.js
        │           │   │   ├── hr.js
        │           │   │   ├── hsb.js
        │           │   │   ├── hu.js
        │           │   │   ├── hy.js
        │           │   │   ├── id.js
        │           │   │   ├── is.js
        │           │   │   ├── it.js
        │           │   │   ├── ja.js
        │           │   │   ├── ka.js
        │           │   │   ├── km.js
        │           │   │   ├── ko.js
        │           │   │   ├── lt.js
        │           │   │   ├── lv.js
        │           │   │   ├── mk.js
        │           │   │   ├── ms.js
        │           │   │   ├── nb.js
        │           │   │   ├── ne.js
        │           │   │   ├── nl.js
        │           │   │   ├── pl.js
        │           │   │   ├── ps.js
        │           │   │   ├── pt-BR.js
        │           │   │   ├── pt.js
        │           │   │   ├── ro.js
        │           │   │   ├── ru.js
        │           │   │   ├── sk.js
        │           │   │   ├── sl.js
        │           │   │   ├── sq.js
        │           │   │   ├── sr-Cyrl.js
        │           │   │   ├── sr.js
        │           │   │   ├── sv.js
        │           │   │   ├── th.js
        │           │   │   ├── tk.js
        │           │   │   ├── tr.js
        │           │   │   ├── uk.js
        │           │   │   ├── vi.js
        │           │   │   ├── zh-CN.js
        │           │   │   └── zh-TW.js
        │           │   ├── LICENSE.md
        │           │   ├── select2.full.js
        │           │   └── select2.full.min.js
        │           └── xregexp
        │               ├── LICENSE.txt
        │               ├── xregexp.js
        │               └── xregexp.min.js
        ├── css
        │   ├── main.e7772a38.css
        │   └── main.e7772a38.css.map
        ├── js
        │   ├── main.d825d148.js
        │   ├── main.d825d148.js.LICENSE.txt
        │   └── main.d825d148.js.map
        ├── media
        │   ├── add.ebf598626c6f9b2211b0578a435aaa6b.svg
        │   └── arrow-left.b553318e4fdaed1113efb091889b7f47.svg
        └── rest_framework
            ├── css
            │   ├── bootstrap-theme.min.css
            │   ├── bootstrap-theme.min.css.map
            │   ├── bootstrap-tweaks.css
            │   ├── bootstrap.min.css
            │   ├── bootstrap.min.css.map
            │   ├── default.css
            │   ├── font-awesome-4.0.3.css
            │   └── prettify.css
            ├── docs
            │   ├── css
            │   │   ├── base.css
            │   │   ├── highlight.css
            │   │   └── jquery.json-view.min.css
            │   ├── img
            │   │   ├── favicon.ico
            │   │   └── grid.png
            │   └── js
            │       ├── api.js
            │       ├── highlight.pack.js
            │       └── jquery.json-view.min.js
            ├── fonts
            │   ├── fontawesome-webfont.eot
            │   ├── fontawesome-webfont.svg
            │   ├── fontawesome-webfont.ttf
            │   ├── fontawesome-webfont.woff
            │   ├── glyphicons-halflings-regular.eot
            │   ├── glyphicons-halflings-regular.svg
            │   ├── glyphicons-halflings-regular.ttf
            │   ├── glyphicons-halflings-regular.woff
            │   └── glyphicons-halflings-regular.woff2
            ├── img
            │   ├── glyphicons-halflings-white.png
            │   ├── glyphicons-halflings.png
            │   └── grid.png
            └── js
                ├── ajax-form.js
                ├── bootstrap.min.js
                ├── coreapi-0.1.1.js
                ├── csrf.js
                ├── default.js
                ├── jquery-3.5.1.min.js
                └── prettify-min.js
```

---

## Prerequisites

- Kubernetes cluster (local or cloud) with metrics-server installed  
- Helm CLI (v3+)  
- `kubectl` CLI configured to access your cluster  
- Docker (for building container images)  

---

## Installation & Deployment

1. **Deploy Helm Chart**

```bash
helm install notesapp notesappchart/ -f notesappchart/values.yaml --namespace nginx --create-namespace
```

2. **Set Kubernetes Namespace Context**

```bash
kubectl config set-context --current --namespace=nginx
```

3. **Verify Deployment**

```bash
kubectl get all
```

---

## Accessing the Application

Forward the service port to your local machine:

```bash
kubectl port-forward svc/notes-app-service 8000:8000
```

Open your browser and visit: [http://localhost:8000](http://localhost:8000)

---

## Auto-scaling with Horizontal Pod Autoscaler (HPA)

The application is configured to auto-scale pods based on CPU utilization (target 80%).

### Load Testing for HPA

Run a load generator pod to simulate traffic:

```bash
kubectl run -i --tty load-generator --rm --image=busybox -n nginx -- /bin/sh
```

Inside the pod shell, run:

```bash
while true; do wget -q -O - http://notes-app-service.nginx.svc.cluster.local:8000; done
```

Watch the HPA status:

```bash
kubectl get hpa
kubectl get pods
```

Press `Ctrl+C` to stop the load generator.

---
## Ingress

Step 1: Install the Ingress-NGINX Controller using Helm
```
helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace
```
Step 2: Verify Installation

```
kubectl get all -n ingress-nginx
NAME                                            READY   STATUS    RESTARTS   AGE
pod/ingress-nginx-controller-68547f7c99-69sns   1/1     Running   0          39s

NAME                                         TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)                      AGE
service/ingress-nginx-controller             LoadBalancer   10.99.174.93   localhost     80:30763/TCP,443:30158/TCP   39s
service/ingress-nginx-controller-admission   ClusterIP      10.96.46.3     <none>        443/TCP                      39s

NAME                                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/ingress-nginx-controller   1/1     1            1           39s

NAME                                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/ingress-nginx-controller-68547f7c99   1         1         1       39s
```

Step 3: Add 127.0.0.1 notesapp.local to your /etc/hosts file if using locally:

```
echo "127.0.0.1 notesapp.local" | sudo tee -a /etc/hosts
```

Step 4: Access the App
```
helm upgrade notesapp ./notesappchart -n nginx
```
Visit the app in your browser:
http://notes.local
