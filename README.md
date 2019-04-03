# Исследования изменения параметров нейронной сети

## Изначальные данные:
```python
MLPClassifier(verbose=True)
Iteration 65, loss = 0.04095003
```
> Итоговая точность 0.9679

Так как на вебинаре были другие результаты, то надо измерить обучение несколько раз, не изменяя параметры обучения. На самом вебинаре, не затрагивался момент что результаты могут быть разными при каждом обучении нейронной сети, не изменяя входящие данные и параметры. Любые изменения буду тестировать 3 раза, из-за отсутствия времени для более подробного изучения влияния изменения параметров.\
\
**Результаты второго запуска обучения**
```python
Iteration 65, loss = 0.03480700
```
> Точность забыл посмотреть.

По количеству итераций результат тот же, по промахам результат отличается, можно сделать выводы что есть погрешности (если правильно их так называть) в обучении при запуске с одними и теми же параметрами.\
\
**Результаты третьего запуска обучения**
```python
Iteration 90, loss = 0.03008237
```
> Итоговая точность 0.8966

Количество итераций сильно изменилось, промахи как и точность тоже изменились.

*Можно сделать выводы, что при учете влияния параметров и подбора их значений, могут быть различные итоговые значения, и возможно нужно несколько раз перепроверять результаты, что все равно не даст гарантии идентичного результата у других.*

Список доступных параметров [MLPClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html), с учетом недостаточно высокого знания английского, могу ошибаться в трактовке:
* hidden_layer_sizes - *По описанию влияет на количество нейронов в скрытом слое. По умолчанию значение (100,).*
* activation - *Если я правильно понимаю, влияет на логику работы в скрытом слое. Принимаемое значение: identity, logistic, tanh, relu. По умолчанию значение 'relu'.*
* solver - *Параметр определяет на то как будет идти работа с данными, есть рекомендуемые параметры для больших (adam) и небольших (lbfgs) наборов. Принимает значения lbfgs, sgd, adam. По умолчанию значение 'adam'.*
* alpha - *Сложно ответить однозначно на что влияет, L2 ограничение? Принимает значение: float. По умолчанию значение 0.0001*
* batch_size - *Регулирует размер minibatch'ей, если solver = lbfgs, то не будут использоваться minibatch'и. Принимает целочисленное значение, если значение авто выбирается наименьшее из двух значений: 200 или кол-во записей при обучении. По умолчанию значение 'auto'.*
* learning_rate - *Влияет на обучение и изменение "веса" значения. Принимаемое значение: constant, invscaling, adaptive. Работает только когда solver = sgd. Значение по умолчанию 'constant'.*
* learning_rate_init - *Регулирует размер шага для изменения "веса" при обучении. Принимаемое значение: double. Работает только когда solver имеет значение 'sgd' или 'adam'. Значение по умолчанию 0.001.*
* power_t - *Влияет на скорость обучения. Принимаемое значение: double. Работает только когда solver имеет значение 'sgd'. Значение по умолчанию 0.5.*
* max_iter - *Максимальное количество итераций. Принимаемое значение: целочисленное значение(int). Значение по умолчанию 200.*
* shuffle - *Перемешивание образцов в каждой итерации. Принимаемое значение: логическое (bool). Работает только когда solver имеет значение 'sgd' или 'adam'. Значение по умолчанию True.*
* random_state - *Начальное число используемое генератором чисел. Принимаемое значение: целочисленное значение(int) или объект типа RandomState или None. Значение по умолчанию None.*
* tol - *Параметр отвечающий за остановку обучения (если правильно понял, погрешность при которой оно останавливается). Принимаемое значение: float. Значение по умолчанию 1e-4.*
* verbose - *Параметр отвечающий за вывод прогресса обучения. Принимаемое значение: логическое (bool). Значение по умолчанию False.*
* warm_start - *Параметр отвечает за инициализацию, используя предыдущее решение. Принимаемое значение: логическое (bool). Значение по умолчанию False.*
* momentum - *Влияет на логику обучения (если я правильно понимаю слово импульс). Принимает значение: float которое имеет значение между числами 0 и 1. Используется когда solver принимает значение 'sgd'. Значение по умолчанию 0.9.*
* nesterovs_momentum - *Влияет на логику обучения (если я правильно понимаю слово импульс). Принимаемое значение: логическое (bool). Используется когда solver принимает значение 'sgd' и momentum > 0. Значение по умолчанию True.*
* early_stopping - *Использовать ли раннее  завершение обучения при незначительных изменениях результата. Принимаемое значение: логическое (bool). Эффективно только когда solver принимает значение 'sgd' или 'adam'.*
* validation_fraction - *Параметр определяющий раннее завершение обучения. Принимает значение: float которое имеет значение между числами 0 и 1. Используется когда early_stopping имеет значение True. Значение по умолчанию 0.1.*
* beta_1 - *Значение влияющее на обучение при solver равном 'adam'. Принимаемое значение: float которое имеет значение между числами 0 и 1. Значение по умолчанию 0.9.*
* beta_2 - *Значение влияющее на обучение при solver равном 'adam'. Принимаемое значение: float которое имеет значение между числами 0 и 1. Значение по умолчанию 0.999.*
* epsilon - *Значение влияющее на обучение при solver равном 'adam'. Принимаемое значение: float. Значение по умолчанию 1e-8.*
* n_iter_no_change - *Максимальное количество итераций без улучшения результата. Принимаемое значение: целочисленное значение(int). Эффективно только когда solver принимает значение 'sgd' или 'adam'. Значение по умолчанию 10.*


## Исследуем влияние параметра shuffle:
*Ожидаемый результаты: Более стабильный результат при отстуствии изменений в настройках нейронной сети. Выставляем значение False, так как по умолчанию значение True.*

**Результат первого запуска:**
```python
MLPClassifier(verbose=True, shuffle=False)
Iteration 76, loss = 0.04453058
```
> Итоговая точность 0.9623

**Результат второго запуска:**
```python
MLPClassifier(verbose=True, shuffle=False)
Iteration 106, loss = 0.04051789
```
> Итоговая точность 0.9652

**Результат третьего запуска:**
```python
MLPClassifier(verbose=True, shuffle=False)
Iteration 92, loss = 0.02903152
```
> Итоговая точность 0.9668

*Вывод изменений: Повторюсь что количество попыток возможно слишком мало чтобы делать однозначные выводы, количество итераций как и точность изменяется. Сильного влияния на точность не замечено.*

## Исследуем влияние параметра hidden_layer_sizes:

**Результат первого запуска со значение 10:**
```python
MLPClassifier(verbose=True, shuffle=False, hidden_layer_sizes=(10,))
Iteration 178, loss = 0.23444384
```
> Итоговая точность 0.9198

**Результат второго запуска со значение 1000:**
```python
MLPClassifier(verbose=True, shuffle=False, hidden_layer_sizes=(1000,))
Iteration 17, loss = 0.12982018
```
> Итоговая точность 0.9689

**Результат третьего запуска со значение 500:**
```python
MLPClassifier(verbose=True, shuffle=False, hidden_layer_sizes=(500,))
Iteration 72, loss = 0.03614241
```
> Итоговая точность 0.98

*Вывод: Уменьшение негативно сказывается на точность, увеличение до какого-то момента повышает точность, но эффективность имеет порог. Дальше будем тестировать со значение 100, так как обучение происходит быстрее. Но для максимального значения, стоит увеличить это значение.*

## Исследуем влияние параметра activation:

**Результат первого запуска со значение 'identity':**
```python
MLPClassifier(verbose=True, shuffle=False, activation='identity')
Iteration 77, loss = 0.33133089
```
> Итоговая точность 0.9137

**Результат второго запуска со значение 'logistic':**
```python
MLPClassifier(verbose=True, shuffle=False, activation='logistic')
Iteration 93, loss = 0.11715823
```
> Итоговая точность 0.9554

**Результат третьего запуска со значение 'tanh':**
```python
MLPClassifier(verbose=True, shuffle=False, activation='tanh')
Iteration 98, loss = 0.14594095
```
> Итоговая точность 0.9495

**Результат четвертого запуска со значение 'relu':**
```python
MLPClassifier(verbose=True, shuffle=False, activation='relu')
Iteration 52, loss = 0.04169335
```
> Итоговая точность 0.9644

*Вывод: Значение 'relu', показало себя наиболее эффективно.*

## Исследуем влияние параметра solver:

**Результат первого запуска со значение 'sgd':**
```python
MLPClassifier(verbose=True, shuffle=False, solver='sgd')
Iteration 165, loss = 0.13789328
```
> Итоговая точность 0.9368

**Результат второго запуска со значение 'lbfgs':**
```python
MLPClassifier(verbose=True, shuffle=False, solver='lbfgs')
```
> Итоговая точность 0.9376

*Вывод: Стандартное значение 'adam', является оптимальным.*

## Исследуем влияние параметра alpha:

**Результат первого запуска со значение 0.001:**
```python
MLPClassifier(verbose=True, shuffle=False, alpha=0.001)
Iteration 83, loss = 0.03026139
```
> Итоговая точность 0.9648

**Результат второго запуска со значение 0.00001:**
```python
MLPClassifier(verbose=True, shuffle=False, alpha=0.00001)
Iteration 102, loss = 0.02752231
```
> Итоговая точность 0.9628

*Вывод: Влияние не замечено.*

## Исследуем влияние параметра batch_size:

**Результат первого запуска со значение 10:**
```python
MLPClassifier(verbose=True, shuffle=False, batch_size=10)
Iteration 80, loss = 0.25601819
```
> Итоговая точность 0.9204

*Замечено значительное увеличение времени обучения. (Наверное больше часа на моей платформе)*

**Результат второго запуска со значение 1000:**
```python
MLPClassifier(verbose=True, shuffle=False, batch_size=1000)
Iteration 46, loss = 0.02664338
```
> Итоговая точность 0.9488

**Результат третьего запуска со значение 10000, необходимо изменить параметр максимального количества итераций:**
```python
MLPClassifier(verbose=True, shuffle=False, batch_size=10000, max_iter=1000)
Iteration 282, loss = 0.00274089
```
> Итоговая точность 0.9397

*Вывод: Увеличение положительно сказывается на производительности, более быстрое обучение. Увеличение сказывается на точности в лучшую сторону до какого-то момента.*

## Исследуем влияние параметра learning_rate:

**Результат первого запуска со значение 'invscaling' ():**
```python
MLPClassifier(verbose=True, shuffle=False, solver='sgd', learning_rate='invscaling', max_iter=1000)
```
*Прервал, было больше 600 итераций, много времени.*
> Итоговая точность 0.8031 (но обучение было прервано)

**Результат второго запуска со значение 'adaptive':**
```python
MLPClassifier(verbose=True, shuffle=False, solver='sgd', learning_rate='adaptive', max_iter=1000)
Iteration 287, loss = 0.12986816
```
> Итоговая точность 0.9362

*Вывод: Есть положительные изменения, но не конкурирует с solver = 'adam'*

## Исследуем влияние параметра learning_rate_init:

**Результат первого запуска со значение 0.01:**
```python
MLPClassifier(verbose=True, shuffle=False, learning_rate_init=0.01)
Iteration 17, loss = 0.89917726
```
> Итоговая точность 0.6299

**Результат первого запуска со значение 0.0001:**
```python
MLPClassifier(verbose=True, shuffle=False, learning_rate_init=0.0001)
Iteration 72, loss = 0.00763919
```
> Итоговая точность 0.9569

*Вывод: Чем меньше значение, тем точнее определение.*

## Параметр power_t
*Пропускаем из-за нехватки времени для тестирования.*

## Параметр max_iter
*Не влияет на точность.*

## Параметр random_state
*Пропускаем из-за нехватки времени для тестирования*

## Параметр tol
*Пропускаем из-за нехватки времени для тестирования*

## Параметр verbose
*Не влияет на точность*

## Параметр warm_start
*Пропускаем из-за нехватки времени для тестирования*

## Параметр momentum
*Пропускаем из-за нехватки времени для тестирования*

## Параметр nesterovs_momentum
*Пропускаем из-за нехватки времени для тестирования*

## Параметр early_stopping
*Пропускаем из-за нехватки времени для тестирования*

## Параметр validation_fraction
*Пропускаем из-за нехватки времени для тестирования*

## Параметр beta_1
*Пропускаем из-за нехватки времени для тестирования*

## Параметр beta_2
*Пропускаем из-за нехватки времени для тестирования*

## Параметр epsilon
*Пропускаем из-за нехватки времени для тестирования*

## Параметр n_iter_no_change
*Пропускаем из-за нехватки времени для тестирования*

## Выводы
*При тестировании разнообраных вариантов с hidden_layer_sizes, batch_size, learning_rate_init так как эти параметры сильнее всего влияли на результаты.
Тестировалась комбинация и одиночные варианты данных параметров, наибольшую эффективность показал вариант*
```python
MLPClassifier(verbose=True, shuffle=False, hidden_layer_sizes=(500,))
```
*с результатом 0.98. Так же тестировались варианты hidden_layer_sizes=(100,100), hidden_layer_sizes=(100,100,100), hidden_layer_sizes=(100,100,100,100) и другие, показавшие примерно такой же результат.*
