---
title: '&lt;kontrakt&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454007"
---
# <a name="ltfuturegt"></a>&lt;kontrakt&gt;

Uwzględnij w przyszłości \<> w standardowym nagłówku, aby zdefiniować klasy szablonów i pomocnicze szablony, które upraszczają uruchamianie funkcji — prawdopodobnie w osobnym wątku — i pobierając jego wynik. Wynik jest wartością zwracaną przez funkcję lub wyjątek, który jest emitowany przez funkcję, ale nie jest przechwytywany w funkcji.

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

Funkcja `async` szablonu i klasy `promise` szablonu i `packaged_task` są dostawcami asynchronicznymi. Klasy `future` szablonu i `shared_future` opisują asynchroniczne obiekty zwrotne.

Każda `promise`z klas `future`szablonu, i `shared_future` ma specjalizację dla typu **void** i częściowej specjalizacji do przechowywania i pobierania wartości przez odwołanie. Te specjalizacje różnią się od szablonu podstawowego tylko w sygnaturach i semantyce funkcji, które przechowują i pobierają zwróconą wartość.

Klasy `future` szablonów i `shared_future` nigdy nie blokują w ich destruktorach, z wyjątkiem przypadków, w których zachowano zgodność z poprzednimi wersjami: W przeciwieństwie do wszystkich innych przyszłości, dla `future`— lub ostatnich `shared_future`— które są dołączone do zadania uruchomionego z `std::async`, destruktor blokuje się, jeśli zadanie nie zostało ukończone; oznacza to, że jest blokowane, jeśli ten wątek nie został jeszcze wywołany `.get()` lub `.wait()`a zadanie jest nadal uruchomione. Następująca Uwaga użyteczności została dodana do opisu `std::async` w projekcie standard: "[Uwaga: Jeśli przyszłość uzyskana z klasy std:: async jest przenoszona poza zakres lokalny, inny kod, który używa przyszłości, musi mieć świadomość, że w przyszłości destruktor może zablokować, aby współużytkowany stan stał się gotowy. — koniec notatki] "we wszystkich innych przypadkach `future` i `shared_future` destruktory są wymagane i mają gwarancję, że nigdy nie będą blokowane.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[future, klasa](../standard-library/future-class.md)|Opisuje asynchroniczny obiekt Return.|
|[future_error, klasa](../standard-library/future-error-class.md)|Opisuje obiekt wyjątku, który może być zgłaszany przez metody typów, które `future` zarządzają obiektami.|
|[packaged_task, klasa](../standard-library/packaged-task-class.md)|Opisuje dostawcę asynchronicznego, który jest otoką wywołania i którego sygnatura wywołania `Ty(ArgTypes...)`to. Skojarzony z nim stan asynchroniczny zawiera kopię obiektu, który można wywołać, oprócz potencjalnego wyniku.|
|[promise, klasa](../standard-library/promise-class.md)|Opisuje dostawcę asynchronicznego.|
|[shared_future, klasa](../standard-library/shared-future-class.md)|Opisuje asynchroniczny obiekt Return. W przeciwieństwie do `future` obiektu dostawca asynchroniczny może być skojarzony z dowolną `shared_future` liczbą obiektów.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[is_error_code_enum, struktura](../standard-library/is-error-code-enum-structure.md)|Specjalizacja wskazująca, `future_errc` że jest odpowiednia do `error_code`przechowywania.|
|[uses_allocator, struktura](../standard-library/uses-allocator-structure.md)|Specjalizacja, która zawsze ma wartość true.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Reprezentuje dostawcę asynchronicznego.|
|[future_category](../standard-library/future-functions.md#future_category)|Zwraca odwołanie do `error_category` obiektu, który charakteryzuje błędy, które są skojarzone z `future` obiektami.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Tworzy element `error_code` , który `error_category` zawiera obiekt, który charakteryzuje `future` błędy.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Tworzy element `error_condition` , który `error_category` zawiera obiekt, który charakteryzuje `future` błędy.|
|[swap](../standard-library/future-functions.md#swap)|Wymienia skojarzony stan asynchroniczny jednego `promise` obiektu z innym.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Dostarcza symboliczne nazwy dla błędów zgłaszanych przez `future_error` klasę.|
|[future_status](../standard-library/future-enums.md#future_status)|Dostarcza symboliczne nazwy z przyczyn, które może zwracać funkcja oczekiwania czasowego.|
|[launch](../standard-library/future-enums.md#launch)|Reprezentuje typ maski bitowej, który opisuje możliwe tryby funkcji `async`szablonu.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
