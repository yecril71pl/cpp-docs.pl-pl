---
title: '&lt;future &gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: c852b3040a94035f6a84b1f717c3583fababbb2c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688020"
---
# <a name="ltfuturegt"></a>&lt;future &gt;

Uwzględnij \<future nagłówka standardowego > do definiowania szablonów klas i pomocniczych szablonów, które upraszczają uruchamianie funkcji — prawdopodobnie w osobnym wątku — i pobierając jego wynik. Wynik jest wartością zwracaną przez funkcję lub wyjątek, który jest emitowany przez funkcję, ale nie jest przechwytywany w funkcji.

Ten nagłówek używa środowisko uruchomieniowe współbieżności (ConcRT), aby można było używać go razem z innymi mechanizmami ConcRT. Aby uzyskać więcej informacji na temat ConcRT, zobacz [środowisko uruchomieniowe współbieżności](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
#include <future>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, ten nagłówek jest zablokowany.

*Dostawca asynchroniczny* przechowuje wynik wywołania funkcji. *Asynchroniczny obiekt zwracany* jest używany do pobierania wyniku wywołania funkcji. *Skojarzony stan asynchroniczny* zapewnia komunikację między dostawcą asynchronicznym a jednym lub większą liczbą asynchronicznych obiektów Return.

Program nie tworzy bezpośrednio żadnych skojarzonych asynchronicznych obiektów stanu. Program tworzy dostawca asynchroniczny za każdym razem, gdy potrzebuje jednego i z nich tworzy asynchroniczny obiekt zwrotny, który współużytkuje swój stan asynchroniczny z dostawcą. Dostawcy asynchroniczni i asynchroniczne obiekty zwrotne zarządzają obiektami, które przechowują ich współużytkowany stan asynchroniczny. Gdy ostatni obiekt, który odwołuje się do skojarzonego ze stanem asynchronicznym, zwalnia go, obiekt, który posiada skojarzony stan asynchroniczny, zostanie zniszczony.

Dostawca asynchroniczny lub asynchroniczny obiekt zwracany, który nie ma skojarzonego stanu asynchronicznego, jest *pusty*.

Skojarzony stan asynchroniczny jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

Funkcja szablonu `async` i szablony klas `promise` i `packaged_task` są dostawcami asynchronicznymi. Szablony klas `future` i `shared_future` opisują asynchroniczne obiekty zwrotne.

Każdy z szablonów klas `promise`, `future` i `shared_future` ma specjalizację dla typu **void** i częściowej specjalizacji do przechowywania i pobierania wartości przez odwołanie. Te specjalizacje różnią się od szablonu podstawowego tylko w sygnaturach i semantyce funkcji, które przechowują i pobierają zwróconą wartość.

Szablony klas `future` i `shared_future` nigdy nie są blokowane w ich destruktorach, z wyjątkiem sytuacji, w których jest zachowana zgodność z poprzednimi wersjami: w przeciwieństwie do wszystkich innych przyszłych operacji dla `future` lub ostatnich `shared_future` — które są dołączone do zadania uruchomionego z `std::async` , destruktor blokuje, jeśli zadanie nie zostało ukończone; oznacza to, że blokuje, czy ten wątek nie wywołał jeszcze `.get()` lub `.wait()`, a zadanie jest nadal uruchomione. Następująca Uwaga użyteczności została dodana do opisu `std::async` w wersji Standard: "[Uwaga: Jeśli przyszłość uzyskana z klasy std:: async jest przenoszona poza zakresem lokalnym, inny kod, który używa przyszłości, musi mieć świadomość, że destruktor w przyszłości może blokować Udostępnianie stanie się gotowe. — koniec notatki] "we wszystkich innych przypadkach wymagane są `future` i destruktory `shared_future` i gwarantowane, że nigdy nie będą blokowane.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[future, klasa](../standard-library/future-class.md)|Opisuje asynchroniczny obiekt Return.|
|[future_error, klasa](../standard-library/future-error-class.md)|Opisuje obiekt wyjątku, który może być zgłaszany przez metody typów, które zarządzają `future` obiektów.|
|[packaged_task, klasa](../standard-library/packaged-task-class.md)|Opisuje dostawca asynchroniczny, który jest otoką wywołania i którego sygnatura wywołania jest `Ty(ArgTypes...)`. Skojarzony z nim stan asynchroniczny zawiera kopię obiektu, który można wywołać, oprócz potencjalnego wyniku.|
|[promise, klasa](../standard-library/promise-class.md)|Opisuje dostawcę asynchronicznego.|
|[shared_future, klasa](../standard-library/shared-future-class.md)|Opisuje asynchroniczny obiekt Return. W przeciwieństwie do obiektu `future` dostawca asynchroniczny może być skojarzony z dowolną liczbą obiektów `shared_future`.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[is_error_code_enum, struktura](../standard-library/is-error-code-enum-structure.md)|Specjalizacja wskazująca, że `future_errc` jest odpowiednia do przechowywania `error_code`.|
|[uses_allocator, struktura](../standard-library/uses-allocator-structure.md)|Specjalizacja, która zawsze ma wartość true.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Reprezentuje dostawcę asynchronicznego.|
|[future_category](../standard-library/future-functions.md#future_category)|Zwraca odwołanie do obiektu `error_category`, który charakteryzuje błędy, które są skojarzone z obiektami `future`.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Tworzy `error_code`, który ma obiekt `error_category`, który charakteryzuje `future` błędów.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Tworzy `error_condition`, który ma obiekt `error_category`, który charakteryzuje `future` błędów.|
|[wymiany](../standard-library/future-functions.md#swap)|Wymienia skojarzony stan asynchroniczny jednego `promise` obiektu z innym.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Dostarcza symboliczne nazwy dla błędów zgłaszanych przez klasę `future_error`.|
|[future_status](../standard-library/future-enums.md#future_status)|Dostarcza symboliczne nazwy z przyczyn, które może zwracać funkcja oczekiwania czasowego.|
|[paska](../standard-library/future-enums.md#launch)|Reprezentuje typ maski bitowej, który opisuje możliwe tryby dla funkcji szablonu `async`.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
