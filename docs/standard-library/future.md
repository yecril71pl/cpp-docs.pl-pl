---
title: '&lt;przyszłe&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <future>
dev_langs:
- C++
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140bdea373442e1e987ce30c2421057b9355796b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954021"
---
# <a name="ltfuturegt"></a>&lt;przyszłe&gt;

Dołączyć standardowy nagłówek \<przyszłych > do definiowania klas szablonów i szablonów pomocniczych, które upraszczają uruchomiona funkcja — prawdopodobnie w oddzielnym wątku — i pobierania jej wynik. Wynikiem jest wartość, która jest zwracana przez funkcję lub wyjątek, który jest emitowane przez funkcję, ale nie jest wyłapywany w funkcji.

Środowisko uruchomieniowe współbieżności (ConcRT) korzysta z tego pliku nagłówkowego, aby można go używać razem z innych mechanizmów ConcRT. Aby uzyskać więcej informacji na temat ConcRT zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
#include <future>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, tego pliku nagłówkowego jest zablokowany.

*Dostawcę asynchronicznego* zapisuje wynik wywołania funkcji. *Asynchronicznego zwrotu obiektu* służy do pobierania wyników wywołania funkcji. *Asynchroniczny stan stowarzyszony* zapewnia komunikację między dostawcę asynchronicznego i co najmniej jeden obiekt zwracany asynchronicznego.

Program nie tworzy bezpośrednio wszystkie obiekty stanu stowarzyszonego asynchronicznie. Program tworzy dostawcę asynchronicznego zawsze wtedy, gdy jeden potrzebuje i przy jego użyciu tworzy asynchronicznego zwrotu obiekt, który udostępnia jego asynchronicznie powiązanym stanie z dostawcą. Asynchroniczne dostawców i obiektów zwrotnych asynchronicznego zarządzać obiektów, które utrzymywać ich udostępnionego asynchroniczny stan stowarzyszony. Obiekt, który posiada asynchronicznego stanu stowarzyszonego jest niszczony, kiedy ostatni obiekt, który odwołuje się do asynchronicznego stanu stowarzyszonego zwolni on.

Dostawcę asynchronicznego lub asynchronicznego zwrotu obiekt, który ma nie asynchronicznego stanu stowarzyszonego *pusty*.

Jest asynchronicznego stanu stowarzyszonego *gotowe* tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

Funkcja szablonu `async` klasy szablonu i `promise` i `packaged_task` asynchronicznego dostawców. Klasy szablonów `future` i `shared_future` opisują asynchronicznego zwrotu obiekty.

Każdą z klas szablonu `promise`, `future`, i `shared_future` jest specjalizacją typu **void** i częściowa specjalizacja do przechowywania i pobierania wartości przez odwołanie. Te specjalizacje różnią się od szablonu podstawowego tylko w przypadku podpisów i semantyka funkcje, które przechowują i pobierają zwracanej wartości.

Klasy szablonów `future` i `shared_future` nigdy nie należy zablokować w ich destruktory, z wyjątkiem w przypadku jednego, który jest zachowywana na potrzeby utrzymywania zgodności z poprzednimi wersjami: w przeciwieństwie do innych prognoz dla `future`— lub ostatni `shared_future`— dołączona do zadania wprowadzenie `std::async`, bloki destruktor Jeśli zadanie nie zostało ukończone; oznacza to, blokuje Jeśli tego wątku nie jeszcze wywołana `.get()` lub `.wait()` i nadal jest uruchomione zadanie. Następująca uwaga użyteczność została dodana do opisu `std::async` w standardzie projekt: "[Uwaga: Jeśli stan w przyszłości uzyskany z std::async zostanie przeniesiona poza zakresem lokalnym, inny kod, który używa przyszłość musi być pamiętać, że destruktor przyszłości może blokować udostępniony stan przestanie być gotowy. — uwagi końcowej] "we wszystkich innych przypadkach `future` i `shared_future` destruktory są wymagane i gwarantują blokowania.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[future, klasa](../standard-library/future-class.md)|Opisuje obiekt asynchronicznego zwrotu.|
|[future_error, klasa](../standard-library/future-error-class.md)|Opisuje obiekt wyjątku, który może zostać wygenerowany za pomocą metod, typów, które zarządzają `future` obiektów.|
|[packaged_task, klasa](../standard-library/packaged-task-class.md)|Opisuje dostawcę asynchronicznego, który jest otoką wywołania i ma podpis wywołania `Ty(ArgTypes...)`. Jego asynchronicznie powiązanym stanie przechowuje kopię jego wywoływanego obiektu, oprócz potencjalnym wynik.|
|[promise, klasa](../standard-library/promise-class.md)|Opisuje dostawcę asynchronicznego.|
|[shared_future, klasa](../standard-library/shared-future-class.md)|Opisuje obiekt asynchronicznego zwrotu. W przeciwieństwie `future` obiektu dostawcę asynchronicznego można skojarzyć z dowolną liczbą `shared_future` obiektów.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[is_error_code_enum, struktura](../standard-library/is-error-code-enum-structure.md)|Specjalizacja, która wskazuje, że `future_errc` nadaje się do przechowywania `error_code`.|
|[uses_allocator, struktura](../standard-library/uses-allocator-structure.md)|Specjalizacja, która zawsze prawdziwe.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Reprezentuje dostawcę asynchronicznego.|
|[future_category](../standard-library/future-functions.md#future_category)|Zwraca odwołanie do `error_category` obiektu, który charakteryzuje się błędy, które są skojarzone z `future` obiektów.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Tworzy `error_code` zawierający `error_category` obiektu, który charakteryzuje `future` błędy.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Tworzy `error_condition` zawierający `error_category` obiektu, który charakteryzuje `future` błędy.|
|[swap](../standard-library/future-functions.md#swap)|Wymienia asynchronicznego stanu stowarzyszonego jednego `promise` obiektu z innego.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Dostarcza nazw symbolicznych dla błędów, które są zgłaszane przez `future_error` klasy.|
|[future_status](../standard-library/future-enums.md#future_status)|Dostarcza nazw symbolicznych dla przyczyn, które może zwracać funkcja Przekroczono limit czasu oczekiwania.|
|[launch](../standard-library/future-enums.md#launch)|Reprezentuje typ maski bitów, który opisuje możliwe tryby funkcji szablonu `async`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
