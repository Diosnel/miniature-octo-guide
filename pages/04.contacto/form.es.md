---
title: Contacto
published: true
form:
    name: contact
    fields:
        -
            name: nombre
            placeholder: Nombre
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            placeholder: Email
            type: email
            validate:
                required: true
        -
            name: message
            placeholder: Mensaje
            type: textarea
            validate:
                required: true
        -
            name: g-recaptcha-response
            type: captcha
            recaptcha_site_key: ENTER_YOUR_CAPTCHA_SITE_KEY
            recaptcha_not_validated: 'Captcha not valid!'
            validate:
                required: true
    buttons:
        -
            type: submit
            value: Enviar
        -
            type: reset
            value: Cancelar
    process:
        -
            captcha:
                recaptcha_secret: ENTER_YOUR_CAPTCHA_SECRET_KEY
        -
            email:
                subject: '[Site Contact Form] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Gracias por su mensaje'
        -
            display: thankyou
---

## Formulario de contacto