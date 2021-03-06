# Компонент StatusButton

Довольно часто front-end разработчикам в своих проектах приходится решать проблему асинхронных состояний. Рассмотрим такой пример: форма заказа.

Пользователь выбирает товар, выбирает его количество и нажимает кнопку заказать. В этот момент фронт должен сделать запрос к бекэнду и подтвердить успешность заказа, или выдать ошибку указав на причину отказа. Естественно необходимо предусмотреть такие проблемы как, медленный или даже отвалившийся интернет у пользователя.

Чтобы решить такой кейс можно воспользоваться различными UX способами, один из них: анимированная кнопка с состояниями. 

Вот несколько примеров с Dribbble, как это может выглядеть:
- [https://dribbble.com/shots/2551579-Download-Button](https://dribbble.com/shots/2551579-Download-Button)
- [https://dribbble.com/shots/1461540-Organic-Loading-State](https://dribbble.com/shots/1461540-Organic-Loading-State)
- [https://dribbble.com/shots/2201051-Activate-Button](https://dribbble.com/shots/2201051-Activate-Button)
- [https://dribbble.com/shots/1673204-Submit-Button](https://dribbble.com/shots/1673204-Submit-Button)
![](https://d13yacurqjgara.cloudfront.net/users/767550/screenshots/2228947/sign-up--button.gif)

Естественно, реализовывать такой компонент каждый раз, для каждой формы в проекты, для схожих кейсов в разных проектах не очень бы хотелось. Поэтому давай рассмотрим, каким образом можно обобщить этот Пользовательский Опыт с помощью React компонента. Для условности назовем его StatusButton.

Внутри компонента должено хранится состояние, которое может быть одним из следующих:
- none
- loading
- success
- error

Каждому этому состоянию должен соответствовать внешний вид (View).
Компонент должен иметь какой-то механизм работы с промежуточными состояниями (transitions). 
Компонент должен предоставить интерфейс для прокидывания состояния сверху, а также интерфейса для прокидывания промиса.

Задача: реализовать  такой компонент.

## Решение
> P.S. Так как описание задачи выглядит немного абстрактно, чуть позднее я опишу конкретные интерфейсы и первые шаги для ее решения, а пока попробуйте реализовать ее самостоятельно