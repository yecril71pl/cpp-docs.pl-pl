---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 298d6a512b2863a326bda0670f33fe8f1bda0688
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449409"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Zawiera nagłówek \<standardowej biblioteki C STDLIB. h > i dodaje skojarzone nazwy `std` do przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są `std` deklarowane w przestrzeni nazw.

> [!NOTE]
> \<STDLIB. h > nie zawiera typu **wchar_t**.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<cstdlib >

**Przestrzeń nazw:** std

## <a name="namespace-and-macros"></a>Przestrzeń nazw i makra

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Funkcje tylko do dokumentacji

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funkcje uruchamiania i kończenia

|Funkcja|Opis|
|-|-|
|[_Exit](#_exit)|Kończy program bez używania destruktorów ani zarejestrowanych funkcji.|
|[abort](#abort)|Kończy program bez używania destruktorów.|
|[atexit](#atexit)|Rejestruje funkcję do zakończenia programu.|
|[Opuść](#exit)|Niszczy obiekty ze wątkiem i magazynem statycznym, a następnie zwraca kontrolę.|
|[at_quick_exit](#at_quick_exit)|Rejestruje funkcję bez argumentów do zakończenia programu.|
|[quick_exit](#quick_exit)|Rejestruje funkcję z zachowanymi obiektami do zakończenia działania programu.|
|[getenv](#getenv)|Zobacz standardowe informacje o bibliotece języka C.|
|[system](#system)|Zobacz standardowe informacje o bibliotece języka C.|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Program zostaje zakończony bez wykonywania destruktorów dla obiektów typu automatyczny, wątek lub statyczny czas przechowywania oraz bez wywoływania funkcji zakończonych do `atexit()`. Funkcja `_Exit` jest w bezpiecznym sygnale.

### <a name="abort"></a>Anuluj

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Uwagi

Program zostaje zakończony bez wykonywania destruktorów dla obiektów typu automatyczny, wątek lub statyczny czas przechowywania oraz bez wywoływania funkcji zakończonych do `atexit()`. Funkcja `abort` jest w bezpiecznym sygnale.

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Wartość zwracana

Zero, jeśli rejestracja powiedzie się, jeśli nie powiedzie się.

#### <a name="remarks"></a>Uwagi

Funkcja rejestruje funkcję wskazywaną przez *Func* do wywołania bez argumentów, gdy `quick_exit` jest wywoływana. `at_quick_exit()` Nie określono `at_quick_exit()` , czy wywołanie, które nie występuje, zanim wszystkie `quick_exit` wywołania zakończą się pomyślnie, a `at_quick_exit()` funkcje nie spowodują wyścigu. Kolejność rejestracji może być nieokreślona, jeśli `at_quick_exit` została wywołana z więcej niż jednego wątku, a `at_quick_exit` ponieważ rejestracje różnią się `atexit` od rejestracji, aplikacje mogą wymagać wywołania obu funkcji rejestracji z ten sam argument. Implementacja obsługuje rejestrację co najmniej 32 funkcji.

### <a name="atexit"></a>atexit —

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Uwagi

Funkcja rejestruje funkcję wskazywaną przez Func, która ma zostać wywołana bez argumentów przy normalnym zakończeniu działania programu.  `atexit()` Nie określono `atexit()` , czy wywołanie, które nie występuje, zanim `exit()` wywołanie powiodło się, a `atexit()` funkcje nie spowodują wyścigu. Implementacja obsługuje rejestrację co najmniej 32 funkcji.

#### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli rejestracja kończy się niepowodzeniem, jeśli nie powiedzie się.

### <a name="exit"></a>Opuść

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Uwagi

Najpierw obiekty z okresem przechowywania wątków i skojarzone z bieżącym wątkiem są niszczone.

Następnie obiekty ze statycznym okresem przechowywania są niszczone, a funkcje `atexit` zarejestrowane przez wywołanie są wywoływane. Obiekty automatyczne nie są niszczone w wyniku wywołania `exit()`. Jeśli kontrolka opuszcza zarejestrowana funkcja wywołana `exit` przez, ponieważ funkcja nie dostarcza procedury obsługi dla zgłoszonego wyjątku `std::terminate()` , należy wywołać. Funkcja jest wywoływana za każdym razem, gdy jest zarejestrowana. Obiekty z automatycznym okresem magazynu są niszczone w programie, którego główna funkcja nie zawiera obiektów automatycznych i wykonuje wywołanie `exit()`do. Kontrolę można przenieść bezpośrednio do takiej funkcji Main, zwracając wyjątek, który jest przechwytywany w głównej.

Następnie wszystkie otwarte strumienie języka C (zgodnie z opisem w <cstdio>temacie) z niezapisanymi danymi buforowanymi są opróżniane, wszystkie otwarte strumienie c są zamknięte, a wszystkie pliki utworzone przez wywołanie `tmpfile()` są usuwane.

Na koniec kontrola jest zwracana do środowiska hosta. Jeśli stan ma wartość zero lub EXIT_SUCCESS, zwracany jest formularz o stanie pomyślne zakończenie stanu. Jeśli status ma wartość EXIT_FAILURE, zwracana jest postać zdefiniowana przez implementację kończenia niepowodzenia stanu. W przeciwnym razie zwrócony stan jest zdefiniowany przez implementację.

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Funkcje zarejestrowane przez wywołania `at_quick_exit` są wywoływane w odwrotnej kolejności rejestracji, z tą różnicą, że funkcja jest wywoływana po wszelkich wcześniej zarejestrowanych funkcjach, które zostały już wywołane w chwili rejestracji. Obiekty nie są niszczone w wyniku wywołania `quick_exit`. Jeśli kontrolka opuszcza zarejestrowana funkcja wywołana `quick_exit` przez, ponieważ funkcja nie dostarcza procedury obsługi dla zgłoszonego wyjątku `std::terminate()` , należy wywołać. Funkcja zarejestrowana za `at_quick_exit` pośrednictwem jest wywoływana przez wątek `quick_exit`wywołujący, który może być innym wątkiem niż ten, który go zarejestrował, dlatego zarejestrowane funkcje nie należy polegać na tożsamości obiektów z okresem przechowywania wątków. Po wywołaniu funkcji `quick_exit` zarejestrowanych należy wywołać metodę `_Exit(status)`. Standardowe bufory plików nie są opróżniane. Funkcja `quick_exit` jest bezpieczna sygnałem, gdy funkcje zarejestrowane w `at_quick_exit` są.

### <a name="system"></a>systemami

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funkcje alokacji pamięci

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

#### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Funkcje konwersji ciągów wielobajtowych/szerokich i znaków

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="algorithm-functions"></a>Funkcje algorytmu

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="low-quality-random-number-generation-functions"></a>Funkcje generowania liczb losowych o niskiej jakości

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="absolute-values"></a>Wartości bezwzględne

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="functions"></a>Funkcje

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
