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
ms.openlocfilehash: c365b5cab5814d3992e6570949a69fc5d39c1dd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373465"
---
# <a name="safeint-class"></a>SafeInt — Klasa

Rozszerza pierwotne liczby całkowite, aby zapobiec przepełnieniu liczby całkowitej i umożliwia porównywanie różnych typów liczby całkowitych.

> [!NOTE]
> Najnowsza wersja tej biblioteki [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)znajduje się pod adresem .

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

| Szablon  |  Opis |
|--------|------------|
| T         |  Typ parametru całkowitej lub logicznej, który `SafeInt` zastępuje. |
| E         |  Wyliczony typ danych definiujący zasady obsługi błędów. |
| U         |  Typ parametru liczby całkowitej lub logicznej dla pomocniczego operandu. |

| Parametr  |  Opis |
|---------|-----------------|
| *Rhs*      |  [w] Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |
| *I*        |  [w] Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |
| *Bitów*     |  [w] Parametr wejściowy, który reprezentuje wartość po prawej stronie operatora w kilku funkcjach autonomicznych. |

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
| podpisany znak       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| niepodpisane __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| niepodpisane __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| niepodpisane __int64  |  `operator unsigned __int64() const` |
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

Klasa `SafeInt` chroni przed przepełnieniem liczby całkowitej w operacjach matematycznych. Rozważmy na przykład dodanie dwóch 8-bitowych liczby całkowite: jeden ma wartość 200, a drugi ma wartość 100. Prawidłowa operacja matematyczna będzie 200 + 100 = 300. Jednak ze względu na 8-bitowy limit liczby całkowitej, górny bit zostanie utracony, a kompilator zwróci 44 (300 - 2<sup>8)</sup>w wyniku. Każda operacja, która zależy od tego równania matematycznego wygeneruje nieoczekiwane zachowanie.

Klasa `SafeInt` sprawdza, czy występuje przepełnienie arytmetyczne lub czy kod próbuje podzielić przez zero. W obu przypadkach klasa wywołuje program obsługi błędów, aby ostrzec program o potencjalnym problemie.

Ta klasa umożliwia również porównanie dwóch różnych typów liczby całkowitej, tak długo, jak są `SafeInt` one obiekty. Zazwyczaj podczas porównywania należy najpierw przekonwertować liczby na ten sam typ. Rzutowanie jednej liczby na inny typ często wymaga sprawdzenia, aby upewnić się, że nie ma utraty danych.

W tabeli Operatorzy w tym temacie wymieniono `SafeInt` operatory matematyczne i porównania obsługiwane przez klasę. Większość operatorów matematycznych `SafeInt` zwraca `T`obiekt typu .

Operacje porównania `SafeInt` między typu i integralną mogą być wykonywane w obu kierunkach. Na przykład `SafeInt<int>(x) < y` oba `y> SafeInt<int>(x)` i są prawidłowe i zwróci ten sam wynik.

Wiele operatorów binarnych `SafeInt` nie obsługuje przy użyciu dwóch różnych typów. Jednym z przykładów `&` jest operator. `SafeInt<T, E> & int`jest obsługiwany, `SafeInt<T, E> & SafeInt<U, E>` ale nie jest. W tym drugim przykładzie kompilator nie wie, jaki typ parametru do zwrócenia. Jednym z rozwiązań tego problemu jest rzut drugi parametr z powrotem do typu podstawowego. Za pomocą tych samych parametrów, można to zrobić za pomocą `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> W przypadku operacji bitowych dwa różne parametry powinny mieć ten sam rozmiar. Jeśli rozmiary różnią się, kompilator zda wyjątek [ASSERT.](../mfc/reference/diagnostic-services.md#assert) Wyniki tej operacji nie mogą być zagwarantowane jako dokładne. Aby rozwiązać ten problem, należy rzutować mniejszy parametr, dopóki nie ma takiego samego rozmiaru jak większy parametr.

Dla operatorów shift przesunięcie więcej bitów niż istnieje dla typu szablonu zgłosić wyjątek ASSERT. Nie będzie to miało wpływu w trybie wydania. Mieszanie dwóch typów parametrów SafeInt jest możliwe dla operatorów shift, ponieważ typ zwracany jest taki sam jak typ oryginalny. Liczba po prawej stronie operatora wskazuje tylko liczbę bitów do przesunięcia.

Podczas wykonywania logicznego porównania z SafeInt obiektu, porównanie jest ściśle arytmetyczne. Rozważmy na przykład następujące wyrażenia:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

Pierwsza instrukcja jest rozpoznawana jako **true**, `false`ale druga instrukcja jest rozpoznawana jako . Bitowe negacja 0 jest 0xFFFFFFFFFF. W drugim oświadczeniu domyślny operator porównania porównuje 0xFFFFFFFF do 0xFFFFFFFFFF i uważa je za równe. Operator porównania dla `SafeInt` klasy zdaje sobie sprawę, że drugi parametr jest ujemny, podczas gdy pierwszy parametr jest niepodpisany. W związku z tym chociaż reprezentacja bitów jest identyczna, operator `SafeInt` logiczny zdaje sobie sprawę, że niepodpisana liczba całkowita jest większa niż -1.

Należy zachować ostrożność `SafeInt` podczas korzystania `?:` z klasy wraz z operatorem trójskładnikowego. Należy wziąć pod uwagę następujący wiersz kodu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilator konwertuje go na to:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Jeśli `flag` `false`tak, kompilator zgłasza wyjątek zamiast przypisywania wartości -1 do `x`. W związku z tym, aby uniknąć tego zachowania, poprawny kod do użycia jest następujący wiersz.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T`i `U` może być przypisany typ logiczny, typ znaku lub typ liczby całkowitej. Typy całkowite mogą być podpisane lub niepodpisane i dowolny rozmiar od 8 bitów do 64 bitów.

> [!NOTE]
> Mimo `SafeInt` że klasa akceptuje wszelkiego rodzaju liczby całkowitej, wykonuje bardziej efektywnie z niepodpisanych typów.

`E`jest mechanizmem obsługi `SafeInt` błędów, który używa. Dwa mechanizmy obsługi błędów są dostarczane z biblioteki SafeInt. Domyślna zasada `SafeIntErrorPolicy_SafeIntException`jest , który zgłasza [SafeIntException wyjątek klasy,](../safeint/safeintexception-class.md) gdy wystąpi błąd. Inne zasady `SafeIntErrorPolicy_InvalidParameter`to , który zatrzymuje program w przypadku wystąpienia błędu.

Istnieją dwie opcje dostosowywania zasad błędów. Pierwszą opcją jest ustawienie `E` parametru `SafeInt`podczas tworzenia pliku . Użyj tej opcji, jeśli chcesz zmienić zasady `SafeInt`obsługi błędów tylko dla jednego . Inną opcją jest zdefiniowanie _SAFEINT_DEFAULT_ERROR_POLICY do niestandardowej klasy obsługi błędów `SafeInt` przed dołączeniem biblioteki. Użyj tej opcji, jeśli chcesz zmienić domyślne zasady `SafeInt` obsługi błędów dla wszystkich wystąpień klasy w kodzie.

> [!NOTE]
> Dostosowana klasa, która obsługuje błędy z biblioteki SafeInt nie należy zwracać kontroli do kodu, który wezwał do obsługi błędów. Po wywołaniu obsługi błędów wynik `SafeInt` operacji nie może być zaufany.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeInt`

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Obszar nazw:** msl::utilities

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt::SafeInt

Konstruuje `SafeInt` obiekt.

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

*I*<br/>
[w] Wartość dla nowego `SafeInt` obiektu. Musi to być parametr typu T lub U, w zależności od konstruktora.

*B*<br/>
[w] Wartość logiczna dla `SafeInt` nowego obiektu.

*U*<br/>
[w] A `SafeInt` typu U. Nowy `SafeInt` obiekt będzie miał taką samą wartość jak *u*, ale będzie typu T.

U Typ danych przechowywanych `SafeInt`w pliku . Może to być typ logiczny, znak lub liczba całkowita. Jeśli jest to typ liczby całkowitej, może być podpisany lub niepodpisany i mieć od 8 do 64 bitów.

### <a name="remarks"></a>Uwagi

Parametr wejściowy konstruktora *i* lub *u*musi być typem logicznym, znakowym lub całkowitym. Jeśli jest to inny typ `SafeInt` parametru, klasa wywołuje [static_assert](../cpp/static-assert.md) wskazać nieprawidłowy parametr wejściowy.

Konstruktory korzystające `U` z typu szablonu automatycznie konwertują parametr wejściowy na typ określony przez `T`program . Klasa `SafeInt` konwertuje dane bez utraty danych. Raportuje do obsługi `E` błędów, jeśli nie `T` można przekonwertować danych na typ bez utraty danych.

Jeśli utworzysz `SafeInt` z parametru logicznego, należy natychmiast zainicjować wartość. Nie można `SafeInt` skonstruować `SafeInt<bool> sb;`przy użyciu kodu . Spowoduje to wygenerowanie błędu kompilacji.
