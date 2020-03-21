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
ms.openlocfilehash: c69dc7ed5e34d98d5acff8f2bc28c34761bd31c6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076819"
---
# <a name="safeint-class"></a>SafeInt — Klasa

Rozszerza elementy pierwotne całkowite, aby zapobiec przepełnieniu liczby całkowitej i umożliwia porównywanie różnych typów liczb całkowitych.

> [!NOTE]
> Najnowsza wersja tej biblioteki znajduje się w [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

| Szablon  |  Opis |
|--------|------------|
| T         |  Typ liczby całkowitej lub parametru logicznego, który `SafeInt` zastępuje. |
| E         |  Wyliczany typ danych, który definiuje zasady obsługi błędów. |
| U         |  Typ liczby całkowitej lub parametru logicznego operandu pomocniczego. |

| Parametr  |  Opis |
|---------|-----------------|
| *RHS*      |  podczas Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |
| *i*        |  podczas Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |
| *bitów*     |  podczas Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Name (Nazwa)                          |  Opis |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Konstruktor domyślny. |

### <a name="assignment-operators"></a>Operatory przypisania

| Name (Nazwa)  |  Składnia |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Operatory rzutowania

| Name (Nazwa)              |  Składnia |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| znak ze znakiem       |  `operator signed char() const` |
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

| Name (Nazwa)  |  Składnia |
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

| Name (Nazwa)  |  Składnia |
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

| Name (Nazwa)     |  Składnia |
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

Klasa `SafeInt` chroni przed przepełnieniem liczby całkowitej w operacjach matematycznych. Na przykład rozważ dodanie dwóch 8-bitowych liczb całkowitych: jeden ma wartość 200, a drugi ma wartość 100. Poprawną operacją matematyczną byłaby 200 + 100 = 300. Jednak ze względu na 8-bitowy limit liczby całkowitej, górny bit zostanie utracony, a kompilator zwróci 44 (300-2<sup>8</sup>) jako wynik. Wszelkie operacje, które są zależne od tego równania matematycznego, spowodują wygenerowanie nieoczekiwanego zachowania.

Klasa `SafeInt` sprawdza, czy występuje przepełnienie arytmetyczne, czy też kod próbuje podzielić przez zero. W obu przypadkach Klasa wywołuje procedurę obsługi błędów, aby ostrzec program o potencjalnym problemie.

Ta klasa pozwala także porównać dwa różne typy liczb całkowitych, o ile są one `SafeInt` obiektów. Zwykle podczas przeprowadzania porównania należy najpierw skonwertować liczby na ten sam typ. Rzutowanie jednej liczby na inny typ często wymaga sprawdzenia, aby upewnić się, że dane nie są tracone.

W tabeli Operators w tym temacie wymieniono operatory matematyczne i porównania obsługiwane przez klasę `SafeInt`. Większość operatorów matematycznych zwraca obiekt `SafeInt` typu `T`.

Operacje porównania między `SafeInt` i typem całkowitym można wykonać w dowolnym kierunku. Na przykład zarówno `SafeInt<int>(x) < y`, jak i `y> SafeInt<int>(x)` są prawidłowe i zwracają ten sam wynik.

Wiele operatorów binarnych nie obsługuje korzystania z dwóch różnych typów `SafeInt`. Przykładem jest operator `&`. `SafeInt<T, E> & int` jest obsługiwana, ale `SafeInt<T, E> & SafeInt<U, E>` nie jest. W tym ostatnim przykładzie kompilator nie wie, jakiego typu parametru zwrócić. Jednym z rozwiązań tego problemu jest rzutowanie drugiego parametru z powrotem na typ podstawowy. Korzystając z tych samych parametrów, można to zrobić za pomocą `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> Dla każdej operacji bitowej dwa różne parametry powinny mieć ten sam rozmiar. Jeśli rozmiary różnią się, kompilator zgłosi wyjątek [.](../mfc/reference/diagnostic-services.md#assert) Nie można zagwarantować dokładności wyników tej operacji. Aby rozwiązać ten problem, należy rzutować mniejszy parametr, dopóki nie jest to ten sam rozmiar, co większy parametr.

Dla operatorów przesunięcia, przesunięcie większej liczby bitów niż istnieje dla typu szablonu spowoduje zgłoszenie wyjątku potwierdzenia. Nie będzie to miało wpływu na tryb zwolnienia. Mieszanie dwóch typów parametrów SafeInt jest możliwe dla operatorów przesunięcia, ponieważ typ zwracany jest taki sam jak typ oryginalny. Liczba po prawej stronie operatora wskazuje tylko liczbę bitów do przesunięcia.

W przypadku wykonywania porównania logicznego z obiektem SafeInt porównanie jest wyłącznie arytmetyczne. Rozważmy na przykład następujące wyrażenia:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

Pierwsza instrukcja jest rozpoznawana jako **true**, ale druga instrukcja jest rozpoznawana jako `false`. Negacja koniunkcji 0 to 0xFFFFFFFF. W drugiej instrukcji operator porównania domyślnego porównuje 0xFFFFFFFF z 0xFFFFFFFF i traktuje je jako równe. Operator porównania dla klasy `SafeInt` realizuje, że drugi parametr jest ujemny, podczas gdy pierwszy parametr jest niepodpisany. W związku z tym mimo że reprezentacja bitowa jest identyczna, operator logiczny `SafeInt` realizuje, że liczba całkowita bez znaku jest większa niż-1.

Należy zachować ostrożność w przypadku używania klasy `SafeInt` wraz z operatorem "Trzyelementowy `?:`". Rozważmy następujący wiersz kodu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilator konwertuje ten element:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Jeśli `flag` jest `false`, kompilator zgłasza wyjątek zamiast przypisywania wartości-1 do `x`. W związku z tym, aby uniknąć tego zachowania, prawidłowy kod, który ma być używany, to poniższy wiersz.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

do `T` i `U` można przypisać typ Boolean, typ znaku lub typ całkowity. Typy całkowite mogą być podpisane lub niepodpisane oraz mieć dowolny rozmiar z 8 bitów do 64 bitów.

> [!NOTE]
> Chociaż Klasa `SafeInt` akceptuje dowolnego rodzaju liczbę całkowitą, jest bardziej wydajna z niepodpisanymi typami.

`E` jest mechanizmem obsługi błędów, którego `SafeInt` używa. Z biblioteką SafeInt są dostarczane dwa mechanizmy obsługi błędów. Domyślne zasady są `SafeIntErrorPolicy_SafeIntException`, co powoduje wyrzucanie wyjątku [klasy SafeIntException](../safeint/safeintexception-class.md) w przypadku wystąpienia błędu. Inne zasady są `SafeIntErrorPolicy_InvalidParameter`, co powoduje zatrzymanie programu w przypadku wystąpienia błędu.

Istnieją dwie opcje dostosowywania zasad błędów. Pierwsza opcja polega na ustawieniu parametru `E` podczas tworzenia `SafeInt`. Użyj tej opcji, jeśli chcesz zmienić zasady obsługi błędów dla tylko jednego `SafeInt`. Druga opcja polega na zdefiniowaniu _SAFEINT_DEFAULT_ERROR_POLICY jako dostosowanej klasy obsługi błędów przed dołączeniem biblioteki `SafeInt`. Użyj tej opcji, jeśli chcesz zmienić domyślne zasady obsługi błędów dla wszystkich wystąpień klasy `SafeInt` w kodzie.

> [!NOTE]
> Dostosowana Klasa, która obsługuje błędy z biblioteki SafeInt, nie powinna zwracać kontroli do kodu, który wywołał procedurę obsługi błędów. Po wywołaniu programu obsługi błędów wynik operacji `SafeInt` nie może być godny zaufania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeInt`

## <a name="requirements"></a>Wymagania

**Nagłówek:** SafeInt. h

**Przestrzeń nazw:** MSL:: Utilities

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt:: SafeInt

Konstruuje obiekt `SafeInt`.

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
podczas Wartość nowego obiektu `SafeInt`. Ta wartość musi być parametrem typu T lub U, w zależności od konstruktora.

*b*<br/>
podczas Wartość logiczna dla nowego obiektu `SafeInt`.

*'t*<br/>
podczas `SafeInt` typu U. Nowy obiekt `SafeInt` będzie mieć taką samą wartość jak *u*, ale będzie typu t.

Typ danych przechowywanych w `SafeInt`. Może to być typ Boolean, znak lub liczba całkowita. Jeśli jest to typ liczba całkowita, może być podpisany lub niepodpisany i zawierać od 8 do 64 bitów.

### <a name="remarks"></a>Uwagi

Parametr wejściowy dla konstruktora, *i* lub *u*musi być typu Boolean, Character lub Integer. Jeśli jest to inny typ parametru, Klasa `SafeInt` wywołuje [static_assert](../cpp/static-assert.md) , aby wskazać nieprawidłowy parametr wejściowy.

Konstruktory używające typu szablonu `U` automatycznie przekonwertują parametr wejściowy na typ określony przez `T`. Klasa `SafeInt` konwertuje dane bez utraty danych. Raport jest raportowany do procedury obsługi błędów `E`, jeśli nie może przekonwertować danych na typ `T` bez utraty danych.

Jeśli utworzysz `SafeInt` z parametru Boolean, musisz natychmiast zainicjować wartość. Nie można utworzyć `SafeInt` przy użyciu `SafeInt<bool> sb;`kodu. Spowoduje to wygenerowanie błędu kompilacji.
