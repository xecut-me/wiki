# idm.xecut.me - OpenID Connect на KanIDM

## Home Assistant: вход с телефона

1. Оставь приложение открытым на экране с шестизначным кодом.
2. На компьютере открой [haos.xecut.me](https://haos.xecut.me/) в приватном окне → автоматический переход на **idm.xecut.me** → войди через **Kanidm**.

   ![Вход в Kanidm после открытия haos.xecut.me](./haos-kanidm-login.webp)

3. После возврата в Home Assistant, на экране **Logged in!**, найди **Use a code from another device**.
4. Введи код с телефона → **Approve login on the other device**.
5. Дождись входа в приложении.

**Не выбирай Continue on this device:** эта кнопка продолжает вход на компьютере. Код вводится в Home Assistant, не в Kanidm.

Если поле не появилось — начни новый вход в приватном окне. Уже открытая сессия Home Assistant не заменяет этот шаг.
