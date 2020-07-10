# tutologin

# Importation des modules

```
from django.shortcuts import render, redirect
from django.contrib.auth import authenticate, login, logout
from django.contrib.auth.decorators import login_required
from django.contrib.auth.models import User
```

## Fonction pour login

````
def connexion(request):
    username = request.POST.get('username', False)
    password = request.POST.get('password', False)

    next = request.POST.get('next', False)
    user = authenticate(username=username, password=password)
    
    if user is not None and user.is_active:
    
        print("user is login")
        """    
        login(request, user)

        if next: 
            return redirect(next)
        else:
            return redirect('homespe') # page si connect
        """
    else:
        return render(request, 'pages/login.html')  # page login
````
## Fonction Logout

````
def deconnexion(request):
    logout(request)

    return redirect('mylogin') # le name de l'url de la page de login
