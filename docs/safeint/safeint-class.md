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
ms.openlocfilehash: 97d81401cfd01d6d39457a9d63c39bc25901128e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219355"
---
# <a name="safeint-class"></a>SafeInt — Klasa

Rozszerza elementy pierwotne całkowite, aby zapobiec przepełnieniu liczby całkowitej i umożliwia porównywanie różnych typów liczb całkowitych.

> [!NOTE]
> Najnowsza wersja biblioteki SafeInt znajduje się w lokalizacji [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Aby użyć biblioteki SafeInt, Sklonuj repozytorium i`#include "SafeInt.hpp"`

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

| Nazwa                          |  Opis |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Konstruktor domyślny. |

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
| znak ze znakiem       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| __int16 bez znaku  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| __int32 bez znaku  |  `operator unsigned __int32() const` |
| długi              |  `operator long() const` |
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

`SafeInt`Klasa chroni przed przepełnieniem liczby całkowitej w operacjach matematycznych. Na przykład rozważ dodanie dwóch 8-bitowych liczb całkowitych: jeden ma wartość 200, a drugi ma wartość 100. Poprawną operacją matematyczną byłaby 200 + 100 = 300. Jednak ze względu na 8-bitowy limit liczby całkowitej, górny bit zostanie utracony, a kompilator zwróci 44 (300-2<sup>8</sup>) jako wynik. Wszelkie operacje, które są zależne od tego równania matematycznego, spowodują wygenerowanie nieoczekiwanego zachowania.

`SafeInt`Klasa sprawdza, czy występuje przepełnienie arytmetyczne, czy kod próbuje podzielić przez zero. W obu przypadkach Klasa wywołuje procedurę obsługi błędów, aby ostrzec program o potencjalnym problemie.

Ta klasa pozwala także porównać dwa różne typy liczb całkowitych, o ile są to `SafeInt` obiekty. Zwykle w przypadku porównania należy najpierw skonwertować liczby na ten sam typ. Rzutowanie jednej liczby na inny typ często wymaga sprawdzenia, aby upewnić się, że dane nie są tracone.

W tabeli Operators w tym temacie wymieniono operatory matematyczne i porównania obsługiwane przez `SafeInt` klasę. Większość operatorów matematycznych zwraca `SafeInt` obiekt typu `T` .

Operacje porównania między `SafeInt` a i typem całkowitym można wykonać w dowolnym kierunku. Na przykład oba `SafeInt<int>(x) < y` i `y> SafeInt<int>(x)` są prawidłowe i zwracają ten sam wynik.

Wiele operatorów binarnych nie obsługuje korzystania z dwóch różnych `SafeInt` typów. Przykładem jest `&` operator. `SafeInt<T, E> & int`jest obsługiwane, ale `SafeInt<T, E> & SafeInt<U, E>` nie jest. W tym ostatnim przykładzie kompilator nie wie, jakiego typu parametru zwrócić. Jednym z rozwiązań tego problemu jest rzutowanie drugiego parametru z powrotem na typ podstawowy. Korzystając z tych samych parametrów, można to zrobić za pomocą polecenia `SafeInt<T, E> & (U)SafeInt<U, E>` .

> [!NOTE]
> Dla każdej operacji bitowej dwa różne parametry powinny mieć ten sam rozmiar. Jeśli rozmiary różnią się, kompilator zgłosi wyjątek [.](../mfc/reference/diagnostic-services.md#assert) Nie można zagwarantować dokładnej wyników tej operacji. Aby rozwiązać ten problem, należy rzutować mniejszy parametr, dopóki nie jest to ten sam rozmiar, co większy parametr.

Dla operatorów przesunięcia, przesunięcie większej liczby bitów niż istnieje dla typu szablonu spowoduje zgłoszenie wyjątku potwierdzenia. Nie będzie to miało wpływu na tryb zwolnienia. Mieszanie dwóch typów parametrów SafeInt jest możliwe dla operatorów przesunięcia, ponieważ typ zwracany jest taki sam jak typ oryginalny. Liczba po prawej stronie operatora wskazuje tylko liczbę bitów do przesunięcia.

W przypadku porównania logicznego z obiektem SafeInt porównanie jest wyłącznie arytmetyczne. Rozważmy na przykład następujące wyrażenia:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

Pierwsza instrukcja jest rozpoznawana jako **`true`** , ale druga instrukcja jest rozpoznawana jako **`false`** . Negacja koniunkcji 0 to 0xFFFFFFFF. W drugiej instrukcji operator porównania domyślnego porównuje 0xFFFFFFFF z 0xFFFFFFFF i traktuje je jako równe. Operator porównania dla `SafeInt` klasy realizuje, że drugi parametr jest ujemny, podczas gdy pierwszy parametr jest niepodpisany. W związku z tym mimo że reprezentacja bitowa jest taka sama, `SafeInt` operator logiczny realizuje, że liczba całkowita bez znaku jest większa niż-1.

Należy zachować ostrożność w przypadku używania `SafeInt` klasy razem z `?:` operatorem Trzyelementowy. Rozważmy następujący wiersz kodu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilator konwertuje ten element:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Jeśli `flag` jest **`false`** , kompilator zgłasza wyjątek zamiast przypisywania wartości-1 do `x` . W związku z tym, aby uniknąć tego zachowania, prawidłowy kod, który ma być używany, to poniższy wiersz.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T`i `U` można przypisać typ Boolean, typ znaku lub typ Integer. Typy całkowite mogą być podpisane lub niepodpisane oraz mieć dowolny rozmiar z 8 bitów do 64 bitów.

> [!NOTE]
> Chociaż `SafeInt` Klasa akceptuje dowolny rodzaj liczby całkowitej, jest bardziej wydajna z niepodpisanymi typami.

`E`jest mechanizmem obsługi błędów, który `SafeInt` używa. Z biblioteką SafeInt są dostarczane dwa mechanizmy obsługi błędów. Zasady domyślne to `SafeIntErrorPolicy_SafeIntException` , które zgłasza wyjątek [klasy SafeIntException](safeintexception-class.md) w przypadku wystąpienia błędu. Inne zasady są `SafeIntErrorPolicy_InvalidParameter` , co powoduje zatrzymanie programu w przypadku wystąpienia błędu.

Istnieją dwie opcje dostosowywania zasad błędów. Pierwsza opcja polega na ustawieniu parametru `E` podczas tworzenia `SafeInt` . Użyj tej opcji, jeśli chcesz zmienić zasady obsługi błędów dla tylko jednego `SafeInt` . Druga opcja polega na zdefiniowaniu _SAFEINT_DEFAULT_ERROR_POLICY jako dostosowanej klasy obsługi błędów przed dołączeniem `SafeInt` biblioteki. Użyj tej opcji, jeśli chcesz zmienić domyślne zasady obsługi błędów dla wszystkich wystąpień `SafeInt` klasy w kodzie.

> [!NOTE]
> Dostosowana Klasa, która obsługuje błędy z biblioteki SafeInt, nie powinna zwracać kontroli do kodu, który wywołał procedurę obsługi błędów. Po wywołaniu programu obsługi błędów wynik `SafeInt` operacji nie może być godny zaufania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeInt`

## <a name="requirements"></a>Wymagania

**Nagłówek:** SafeInt. HPP
> [!NOTE]
> Najnowsza wersja tej biblioteki znajduje się w lokalizacji [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Sklonuj bibliotekę i Dołącz SafeInt. HPP, aby użyć biblioteki SafeInt.
> Preferuj to repozytorium GitHub <SafeInt. h>. jest to Modern wersja <SafeInt. h>, która zawiera niewielką liczbę poprawek błędów, korzysta z nowoczesnych funkcji języka C++, w wyniku czego bardziej wydajny kod i jest przenośna na dowolną platformę przy użyciu oprogramowania w zatoce, Clang lub kompilatorów firmy Intel.

### <a name="example"></a>Przykład

```c
#include "SafeInt.hpp" // set path to your clone of the SafeInt GitHub repo (https://github.com/dcleblanc/SafeInt)

int main()
{
    int divisor = 3;
    int dividend = 6;
    int result;

    bool success = SafeDivide(dividend, divisor, result); // result = 2
    success = SafeDivide(dividend, 0, result); // expect fail. result isn't modified.
}
```

**Przestrzeń nazw:** brak

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt:: SafeInt

Konstruuje `SafeInt` obiekt.

```cpp
SafeInt() throw

SafeInt (const T& i) throw ()

SafeInt (bool b) throw ()

template <typename U>
SafeInt (const SafeInt <U, E>& u)

I template <typename U>
SafeInt (const U& i)
```

### <a name="parameters"></a>Parametry

`i`<br/>
podczas Wartość nowego `SafeInt` obiektu. Ta wartość musi być parametrem typu T lub U, w zależności od konstruktora.

`b`<br/>
podczas Wartość logiczna dla nowego `SafeInt` obiektu.

`u`<br/>
podczas A `SafeInt` typu U. Nowy `SafeInt` obiekt będzie mieć taką samą wartość jak *u*, ale będzie typu T.

`U`Typ danych przechowywanych w `SafeInt` . Może to być typ Boolean, znak lub liczba całkowita. Jeśli jest to typ liczba całkowita, może być podpisany lub niepodpisany i zawierać od 8 do 64 bitów.

### <a name="remarks"></a>Uwagi

Parametr wejściowy dla konstruktora, *i* lub *u*musi być typu Boolean, Character lub Integer. Jeśli jest to inny typ parametru, `SafeInt` Klasa wywołuje [static_assert](../cpp/static-assert.md) , aby wskazać nieprawidłowy parametr wejściowy.

Konstruktory używające typu szablonu `U` automatycznie konwertują parametr wejściowy na typ określony przez `T` . `SafeInt`Klasa konwertuje dane bez utraty danych. Raport jest raportowany do programu obsługi błędów, `E` Jeśli nie może przekonwertować danych na typ `T` bez utraty danych.

W przypadku utworzenia `SafeInt` z parametru Boolean należy natychmiast zainicjować wartość. Nie można skonstruować `SafeInt` przy użyciu kodu `SafeInt<bool> sb;` . Spowoduje to wygenerowanie błędu kompilacji.
