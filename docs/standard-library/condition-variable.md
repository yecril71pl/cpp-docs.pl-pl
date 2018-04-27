---
title: '&lt;condition_variable —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <condition_variable>
dev_langs:
- C++
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ddc3db4d17bdb3b4ff9c8a9e419b59d22b6088d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable —&gt;

Określa klasy [condition_variable —](../standard-library/condition-variable-class.md) i [condition_variable_any —](../standard-library/condition-variable-any-class.md) służące do tworzenia obiektów, które poczekaj, aż warunek miał wartość true.

Ten nagłówek używa współbieżność środowiska wykonawczego (ConcRT), tak aby można go używać razem z innych mechanizmów ConcRT. Aby uzyskać więcej informacji o ConcRT, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
#include <condition_variable>
```

> [!NOTE]
> W kodzie, który ma być kompilowana przy użyciu **/CLR**, ten nagłówek jest zablokowany.

### <a name="remarks"></a>Uwagi

Kod, który oczekuje dla zmiennej warunku należy również użyć `mutex`. Wątek wywołujący musi zablokować `mutex` przed wywołaniem funkcji oczekiwania dla zmiennej stanu. `mutex` Jest następnie zablokowana, gdy wywoływana funkcja zwraca. `mutex` Nie jest zablokowane, gdy wątek oczekuje na warunek miał wartość true. Tak, aby nie są nieprzewidywalne wyniki, każdy wątek, który oczekuje na zmienną warunek musi używać tego samego `mutex` obiektu.

Obiekty typu `condition_variable_any` może być używany z obiektu mutex dowolnego typu. Typ obiektu mutex, który jest używany nie trzeba udostępniać `try_lock` metody. Obiekty typu `condition_variable` można używać tylko z obiektu mutex typu `unique_lock<mutex>`. Obiekty tego typu może być szybsza niż obiekty typu `condition_variable_any<unique_lock<mutex>>`.

Oczekiwania na zdarzenie, najpierw blokady obiektu mutex, a następnie wywołać jeden z `wait` metody zmiennej stanu. `wait` Wywołać bloków, aż inny wątek sygnały zmiennej stanu.

*Fałszywe wakeups* wystąpić, gdy wątków, które oczekują na zmienne warunków zostać odblokowany bez potrzeby powiadomienia. Rozpoznawanie takie fałszywe wakeups, kod, który oczekuje na warunek miał wartość true jawnie należy sprawdzić warunku kod zwrócona przez funkcję oczekiwania. Zwykle odbywa się przy użyciu pętli. można użyć `wait(unique_lock<mutex>& lock, Predicate pred)` Aby wykonać tę pętlę.

```cpp
while (condition is false)
    wait for condition variable;
```

`condition_variable_any` i `condition_variable` klasy każdy ma trzy metody oczekiwania dla warunku.

- `wait` czeka na okres bez ograniczeń.

- `wait_until` czeka, aż do określonej `time`.

- `wait_for` czeka na określoną `time interval`.

Każda z tych metod ma dwie wersje przeciążona. Tylko jedna czeka i wybudzania spuriously. Druga przyjmuje argument dodatkowe szablonu, który definiuje predykatu. Metoda nie zwraca momentu predykatu `true`.

Każda klasa ma również dwie metody, które są używane do powiadamiania warunek zmiennej, która jest jego stan `true`.

- `notify_one` budzi się jeden z wątków, które oczekuje na zmiennej stanu.

- `notify_all` budzi wszystkie wątki, które czekają zmiennej stanu.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable, klasa](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any, klasa](../standard-library/condition-variable-any-class.md)<br/>
