---
title: '&lt;przyszłe&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <future>
dev_langs:
- C++
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02f6268c9f1d7952b61a1d0975b32c151d753da7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltfuturegt"></a>&lt;Przyszłe&gt;

Dołącz nagłówek standardowy \<przyszłych > do definiowania klas szablonów i obsługi szablonów, które upraszczają uruchomiona funkcja — prawdopodobnie w oddzielnym wątku — i pobierania jej wynik. Wynik jest wartością zwróconą przez funkcję lub wyjątek, który jest emitowany przez funkcję, ale nie zawiera funkcji.

Ten nagłówek używa współbieżność środowiska wykonawczego (ConcRT), tak aby można go używać razem z innych mechanizmów ConcRT. Aby uzyskać więcej informacji o ConcRT, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
#include <future>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który ma być kompilowana przy użyciu **/CLR**, ten nagłówek jest zablokowany.

*Asynchroniczne dostawcy* przechowuje wynikiem wywołania funkcji. *Asynchronicznego obiektu zwracanego* służy do pobierania wynikiem wywołania funkcji. *Skojarzony stan asynchronicznego* zapewnia komunikację między dostawcą asynchroniczne i co najmniej jeden obiekt zwracany asynchronicznego.

Program nie tworzy bezpośrednio wszystkie obiekty skojarzony stan asynchronicznego. Program tworzy dostawcę asynchroniczne, musi on a niż tworzy asynchroniczne zwracany obiekt, który udostępnia asynchroniczne stanu skojarzone z dostawcą. Asynchroniczne dostawców i asynchronicznych obiektów zwracanych Zarządzanie obiektów, które przechowywać ich udostępnionego skojarzony stan asynchronicznego. Gdy ostatni obiekt, który odwołuje się do skojarzony stan asynchronicznego zwolnieniem, obiekt, który przechowuje skojarzony stan asynchronicznego zostanie zniszczony.

Asynchroniczne dostawcy lub asynchroniczne zwracanego obiektu, który ma nie skojarzony stan asynchroniczne jest *pusty*.

Jest skojarzony stan asynchronicznego *gotowe* tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.

Funkcja szablonu `async` klasy szablonu i `promise` i `packaged_task` asynchroniczne dostawców. Klasy szablonów `future` i `shared_future` opisano asynchroniczne zwracanych obiektów.

Każda z klas szablonu `promise`, `future`, i `shared_future` ma specjalizacji dla typu `void` i częściowa specjalizacja do przechowywania i pobierania wartość przez odwołanie. Te specjalizacje różnią się od podstawowego szablonu tylko w podpisów i semantykę funkcji, które przechowują i pobierają zwracanej wartości.

Klasy szablonów `future` i `shared_future` nigdy nie bloku w ich destruktory, z wyjątkiem w jeden przypadek, który jest zachowane w celu zgodności z poprzednimi wersjami: w przeciwieństwie do innych prognoz dla `future`— lub ostatni `shared_future`— dołączony do zadania wprowadzenie do `std::async`, bloki destruktora Jeśli zadanie nie zostało ukończone; oznacza to, blokuje Jeśli tego wątku nie jeszcze wywołana `.get()` lub `.wait()` i zadanie jest uruchomione. Poniższe uwagi użyteczność został dodany do opisu `std::async` w standardzie projektu: "[Uwaga: Jeśli przyszłości uzyskane z std::async zostanie przeniesiona poza zakres lokalny, innego kodu, który używa przyszłości musi być pamiętać, że w przyszłości destruktora może blokować Aby gotowa. udostępniony stan — Uwaga zakończenia] "we wszystkich innych przypadkach `future` i `shared_future` destruktory są wymagane i dotrą do nigdy nie blokuj.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[future, klasa](../standard-library/future-class.md)|W tym artykule opisano zwracanego obiektu asynchronicznego.|
|[future_error, klasa](../standard-library/future-error-class.md)|Opisuje obiekt wyjątku, który może zostać wygenerowany przez metody typów, które zarządzają `future` obiektów.|
|[packaged_task, klasa](../standard-library/packaged-task-class.md)|Opisuje dostawcę asynchroniczne wywołanie otoką i których sygnatury wywołania `Ty(ArgTypes...)`. Jego skojarzony stan asynchronicznego przechowuje kopię jego można wywołać obiektu oprócz potencjalnych wyników.|
|[promise, klasa](../standard-library/promise-class.md)|Opisuje dostawcę asynchronicznego.|
|[shared_future, klasa](../standard-library/shared-future-class.md)|W tym artykule opisano zwracanego obiektu asynchronicznego. Contrast z `future` obiekt asynchroniczny dostawcy można skojarzyć z dowolną liczbę `shared_future` obiektów.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[is_error_code_enum, struktura](../standard-library/is-error-code-enum-structure.md)|Specjalizacja, która wskazuje, że `future_errc` nadaje się do przechowywania `error_code`.|
|[uses_allocator, struktura](../standard-library/uses-allocator-structure.md)|Specjalizacja, który zawsze jest spełniony.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Reprezentuje dostawcę asynchronicznego.|
|[future_category](../standard-library/future-functions.md#future_category)|Zwraca odwołanie do `error_category` obiektu, która charakteryzuje się błędy, które są skojarzone z `future` obiektów.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Tworzy `error_code` mający `error_category` obiekt, który charakteryzuje `future` błędy.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Tworzy `error_condition` mający `error_category` obiekt, który charakteryzuje `future` błędy.|
|[swap](../standard-library/future-functions.md#swap)|Zamienia skojarzony stan asynchronicznego jednego `promise` innego obiektu.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Dostarcza nazw symbolicznych, błędów, które są zgłaszane przez `future_error` klasy.|
|[future_status](../standard-library/future-enums.md#future_status)|Dostarcza nazw symbolicznych z powodów zwracających w funkcji czasu oczekiwania.|
|[launch](../standard-library/future-enums.md#launch)|Reprezentuje typ maski, który opisuje możliwe tryby funkcji szablonu `async`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
