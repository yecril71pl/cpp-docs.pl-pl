---
title: SafeInt — Klasa
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: 2ff5aaf2eee84af1b1dddba21560e7b254f00069
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327216"
---
# <a name="safeint-class"></a>SafeInt — Klasa

Umożliwia porównanie różnych typów całkowitych i rozszerza prymitywów liczby całkowitej w celu uniknięcia przepełnienia liczby całkowitej.

> [!NOTE] 
> Najnowszą wersję tej biblioteki znajduje się w [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

| Szablon  |  Opis |
|--------|------------|
| T         |  Typ liczby całkowitej lub parametr logiczny który `SafeInt` zastępuje. |
| E         |  Typ wyliczany danych, który definiuje zasady obsługi błędów. |
| U         |  Typ liczby całkowitej lub parametr logiczny dodatkowej operandu. |

| Parametr  |  Opis |
|---------|-----------------|
| *RHS*      |  [in] Parametr wejściowy, która reprezentuje wartość po prawej stronie operatora w kilka funkcji autonomicznych. |
| *i*        |  [in] Parametr wejściowy, która reprezentuje wartość po prawej stronie operatora w kilka funkcji autonomicznych. |
| *Usługa BITS*     |  [in] Parametr wejściowy, która reprezentuje wartość po prawej stronie operatora w kilka funkcji autonomicznych. |

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                          |  Opis |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Domyślny konstruktor. |

### <a name="assignment-operators"></a>Operatory przypisania

| Nazwa  |  Składnia |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Operatory rzutowania

| Nazwa              |  Składnia |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| podpisany char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| __int16 bez znaku  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| __int32 bez znaku  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| __int64 bez znaku  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Operatory porównania

| Nazwa  |  Składnia |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>Operatory arytmetyczne

| Nazwa  |  Składnia |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>Operatory logiczne

| Nazwa     |  Składnia |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>Uwagi

`SafeInt` Klasy chroni przed całkowitą przepełnienie w operacji matematycznych. Na przykład, należy rozważyć dodanie dwóch 8-bitowych liczb całkowitych: jedna z nich ma wartość 200, a drugi ma wartość 100. Operacja matematyczna poprawne byłoby 200 + 100 = 300. Jednak ze względu na limit 8-bitową liczbę całkowitą, górny bitowej zostaną utracone i kompilator zwróci 44 (300-2<sup>8</sup>) jako wynik. Każdej operacji, która jest zależna od tego równania matematyczne spowoduje wygenerowanie nieoczekiwanego zachowania.

`SafeInt` Klasa sprawdza, czy występuje przepełnienie arytmetyczne lub tego, czy kod próbuje dzielenie przez zero. W obu przypadkach klasa wywołuje procedurę obsługi błędów w celu otrzymania program potencjalnego problemu.

Ta klasa umożliwia również porównać dwa różne typy liczb całkowitych, tak długo, jak są one `SafeInt` obiektów. Zazwyczaj podczas wykonywania porównania, należy najpierw przekonwertować liczby do tego samego typu. Rzutowanie cyfra do innego typu często wymaga kontrole, aby upewnić się, że istnieje bez utraty danych.

W tabeli operatorów, w tym temacie wymieniono operatory matematyczne i porównanie obsługiwanych przez `SafeInt` klasy. Operatory matematyczne najbardziej zwracają `SafeInt` obiektu typu `T`.

Operacje porównania między `SafeInt` i typem całkowitym, mogą być wykonywane w dowolnym kierunku. Na przykład zarówno `SafeInt<int>(x) < y` i `y> SafeInt<int>(x)` są prawidłowe i zwraca ten sam wynik.

Wiele operatorów binarnych nie obsługują przy użyciu dwóch różnych `SafeInt` typów. Przykładem tego jest `&` operatora. `SafeInt<T, E> & int` jest obsługiwany, ale `SafeInt<T, E> & SafeInt<U, E>` nie jest. W drugim przykładzie kompilator nie wiedzieć, jakiego typu parametru do zwrócenia. Jedno rozwiązanie tego problemu jest rzutowanie drugi parametr do typu podstawowego. Za pomocą te same parametry, można to zrobić za pomocą `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> Wszystkie operacje bitowe dwa różne parametry powinna być taki sam rozmiar. Jeśli są różne rozmiary, kompilator będzie sygnalizować [ASERCJA](../mfc/reference/diagnostic-services.md#assert) wyjątku. Wyniki tej operacji nie można zagwarantować muszą być dokładne. Aby rozwiązać ten problem, wykonaj rzutowanie mniejszych parametr, dopóki jest taki sam rozmiar jak większych parametru.

Dla operatorów przesunięcia przesunięcie kilka bitów, nie istnieje dla typu szablonu spowoduje zgłoszenie wyjątku ASSERT. Będzie to miało żadnego efektu w trybie wydania. Operatory przesunięcia możliwe jest mieszanie dwa typy parametrów SafeInt, ponieważ zwracany typ jest taki sam jak oryginalnego typu. Liczba po prawej stronie operatora tylko wskazuje liczbę bitów, aby przesunąć.

Podczas wykonywania logicznych porównania z obiektem SafeInt wynikiem porównania jest ściśle arytmetyczne. Na przykład należy wziąć pod uwagę te wyrażenia:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

Pierwsza instrukcja jest rozpoznawana jako **true**, ale druga instrukcja jest rozpoznawana jako `false`. Negacja 0 jest 0xFFFFFFFF. W drugiej instrukcji domyślny operatora porównania porównuje 0xFFFFFFFF lub 0xFFFFFFFF i traktuje je równe. Operator porównania dla `SafeInt` klasy zdaje sobie sprawę, że drugi parametr jest ujemna, pierwszy parametr jest niepodpisany. W związku z tym, mimo że reprezentacja bit jest identyczna, `SafeInt` operatora logicznego zdaje sobie sprawę, że liczba całkowita bez znaku jest większy niż -1.

Należy zachować ostrożność, korzystając z `SafeInt` klasy wraz z `?:` operator trójargumentowy. Należy wziąć pod uwagę następujący wiersz kodu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilator konwertuje go do poniższego:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Jeśli `flag` jest `false`, kompilator generuje wyjątek zamiast przypisywać wartość -1 do `x`. W związku z tym aby uniknąć tego zachowania, poprawny kod używany jest następujący wiersz.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` i `U` można przypisać typu Boolean, typ znaku lub typ liczby całkowitej. Liczba całkowita, typy, które mogą być podpisane lub niepodpisane i dowolnego rozmiaru, od 8 bitów na 64-bitowy.

> [!NOTE]
> Mimo że `SafeInt` klasy akceptuje dowolnego typu liczby całkowitej, bardziej wydajnie przeprowadza się za pomocą typy bez znaku.

`E` jest mechanizm obsługi błędów, `SafeInt` używa. Biblioteka SafeInt znajdują się dwa mechanizmy obsługi błędów. Domyślne zasady to `SafeIntErrorPolicy_SafeIntException`, który zgłasza [safeintexception — klasa](../windows/safeintexception-class.md) wyjątek po wystąpieniu błędu. Inne zasady są `SafeIntErrorPolicy_InvalidParameter`, który zatrzymuje program, jeśli wystąpi błąd.

Dostępne są dwie opcje, aby dostosować zasady dotyczące błędów. Pierwszym z nich jest można ustawić parametru `E` po utworzeniu `SafeInt`. Użyj tej opcji, jeśli chcesz zmienić obsługi zasad dla co najmniej jeden błędów `SafeInt`. Inną możliwością jest zdefiniowanie _SAFEINT_DEFAULT_ERROR_POLICY być dostosowane klasy obsługi błędów, przed wprowadzeniem `SafeInt` biblioteki. Użyj tej opcji, jeśli chcesz zmienić zasady dla wszystkich wystąpień obsługi błędów, domyślne `SafeInt` klasy w kodzie.

> [!NOTE]
> Niestandardowe klasy, która obsługuje błędy z Biblioteka SafeInt nie powinny zwracać formantu do kodu, który wywołał procedurę obsługi błędów. Po zostanie wywołana procedura obsługi błędów, wynik `SafeInt` operacja nie jest zaufany.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeInt`

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** msl::utilities

## <a name="safeint"></a>SafeInt::SafeInt

Konstruuje `SafeInt` obiektu.

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)
```

### <a name="parameters"></a>Parametry

*i*<br/>
[in] Wartość dla nowej klasy `SafeInt` obiektu. Musi to być parametrem typu T lub U, w zależności od tego konstruktora.

*b*<br/>
[in] Wartość logiczna dla nowej `SafeInt` obiektu.

*u*<br/>
[in] A `SafeInt` z typu U. Nowy `SafeInt` obiekt będzie miał taką samą wartość jak *u*, ale będą typu T.

U typu danych przechowywanych w `SafeInt`. Może to być atrybut typu wartość logiczna, znaku lub liczba całkowita typu. Jeśli typ liczby całkowitej, mogą być podpisane lub niepodpisane i mieć długość od 8 do 64 bitów.

### <a name="remarks"></a>Uwagi

Parametr wejściowy dla konstruktora, *i* lub *u*, musi być typu wartość logiczna, znaku lub liczba całkowita. Jeśli jest innego typu parametru `SafeInt` klasy wywołania [static_assert](../cpp/static-assert.md) do wskazania nieprawidłowy parametr wejściowy.

Konstruktory, które używają typu szablonu `U` automatycznie przekonwertować parametru wejściowego typu określonego przez `T`. `SafeInt` Klasy konwertuje dane bez utraty danych. Wysyła raporty do programu obsługi błędów `E` gdy go nie może przekonwertować danych na typ `T` bez utraty danych.

Jeśli tworzysz `SafeInt` z parametrem logicznym należy zainicjować wartości natychmiast. Nie można skonstruować `SafeInt` przy użyciu kodu `SafeInt<bool> sb;`. Spowoduje to wygenerowanie błędu kompilacji.
