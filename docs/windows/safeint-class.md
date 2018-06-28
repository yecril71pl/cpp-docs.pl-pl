---
title: Safeint — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7715553e17e49ef3c169145abfb49816f6d6dd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891340"
---
# <a name="safeint-class"></a>SafeInt — Klasa
Rozszerza podstawowych liczba całkowita, aby uniknąć przepełnienia całkowitą i umożliwia porównanie różnych typów całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Szablon|Opis|  
|--------------|-----------------|  
|T|Typ integer lub parametrów typu Boolean który `SafeInt` zastępuje.|  
|E|Typ wyliczeniowy danych, który definiuje zasady obsługi błędów.|  
|U|Typ integer lub parametrów typu Boolean operandu dodatkowej.|  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] rhs|Parametr wejściowy, który reprezentuje wartość prawej strony operatora w kilka funkcji autonomicznej.|  
|[w] i|Parametr wejściowy, który reprezentuje wartość prawej strony operatora w kilka funkcji autonomicznej.|  
|[Usługa bits in]|Parametr wejściowy, który reprezentuje wartość prawej strony operatora w kilka funkcji autonomicznej.|  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Domyślny konstruktor.|  
  
### <a name="assignment-operators"></a>Operatory przypisania  
  
|Nazwa|Składnia|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>Operatory rzutowania  
  
|Nazwa|Składnia|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|char podpisem|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|__int16 bez znaku|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|__int32 bez znaku|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|__int64 bez znaku|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>Operatory porównania  
  
|Nazwa|Składnia|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>Operatory arytmetyczne  
  
|Nazwa|Składnia|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>Operatory logiczne  
  
|Nazwa|Składnia|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>Uwagi  
 `SafeInt` Klasy chroni przed całkowitą przepełnienie w operacji matematycznych. Na przykład, Rozważ dodanie dwóch 8-bitowych liczb całkowitych: jeden ma wartość 200, a drugi ma wartość 100. Poprawne działanie matematyczne byłoby 200 + 100 = 300. Jednak ze względu na limit 8-bitową liczbę całkowitą górny bitowej zostaną utracone i kompilator będzie zwracać 44 (300-2<sup>8</sup>) w wyniku. Żadnej operacji, która zależy od tego równanie matematyczne wygeneruje nieoczekiwane zachowanie.  
  
 `SafeInt` Klasa sprawdza, czy występuje przepełnienie arytmetyczne, lub czy kod próbuje dzielenia przez zero. W obu przypadkach klasy wywołuje program obsługi błędów w celu ostrzegania o program potencjalny problem.  
  
 Ta klasa umożliwia także porównać dwa typy liczb całkowitych, tak długo, jak są one `SafeInt` obiektów. Zazwyczaj podczas wykonywania porównanie, najpierw przekonwertuj numerów, aby być tego samego typu. Rzutowanie jeden numer z innym typem często wymaga kontroli, aby upewnić się, że nie jest bez utraty danych.  
  
 W tabeli operatory w tym temacie wymieniono obsługiwane przez operatorów matematycznych i porównanie `SafeInt` klasy. Operatory matematyczne najbardziej zwracać `SafeInt` obiektu typu `T`.  
  
 Operacje porównania między `SafeInt` typem całkowitym można wykonywać w żadnym kierunku. Na przykład zarówno `SafeInt<int>(x) < y` i `y> SafeInt<int>(x)` są prawidłowe i zwraca ten sam rezultat.  
  
 Za pomocą dwóch różnych nie obsługują wielu operatorów binarnych `SafeInt` typów. Przykładem tego jest `&` operatora. `SafeInt<T, E> & int` jest obsługiwana, ale `SafeInt<T, E> & SafeInt<U, E>` nie jest. W drugim przykładzie kompilator nie wiedzieć, jakiego typu parametru do zwrócenia. Jedno rozwiązanie tego problemu jest rzutowanie drugi parametr do typu podstawowego. Przy użyciu tych samych parametrach, można to zrobić z `SafeInt<T, E> & (U)SafeInt<U, E>`.  
  
> [!NOTE]
>  Dla dowolnego Operacje bitowe dwa różne parametry powinny mieć taki sam rozmiar. Jeśli są różne rozmiary, kompilator zgłosi [ASSERT](../mfc/reference/diagnostic-services.md#assert) wyjątku. Wyniki tej operacji nie można zagwarantować za obowiązujące. Aby rozwiązać ten problem, wykonaj rzutowanie mniejszych parametru dopóki jest taki sam rozmiar jak parametr większy.  
  
 Dla operatorów shift przesunięcie bitów więcej niż istnieje dla typu szablonu spowoduje zgłoszenie wyjątku potwierdzenia. To nie odniesie żadnego skutku w trybie wersji. Operatory przesunięcia możliwe jest mieszanie dwa typy parametrów safeint —, ponieważ typ zwracany jest taka sama jak oryginalny typ. Liczba po prawej stronie operatora tylko wskazuje liczbę bitów, które mają zostać przesunięte.  
  
 Podczas wykonywania logicznej porównanie z obiektem safeint — porównanie jest ściśle arytmetyczne. Rozważmy na przykład tych wyrażeń:  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 Pierwsza instrukcja jest rozpoznawana jako `true`, ale druga instrukcja jest rozpoznawana jako `false`. Bitową negację 0 jest 0xFFFFFFFF. W drugim instrukcji domyślnego operatora porównania porównuje 0xFFFFFFFF do 0xFFFFFFFF i traktuje je takie same. Operator porównania dla `SafeInt` klasy realizuje drugi parametr jest ujemna, podczas gdy pierwszy parametr nie jest podpisany. W związku z tym, mimo że reprezentacja bit jest identyczna, `SafeInt` operatora logicznego realizuje, że liczba całkowita bez znaku jest większy niż -1.  
  
 Należy zachować ostrożność, korzystając z `SafeInt` klasy razem z `?:` trójargumentowy. Rozważmy następujący wiersz kodu.  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 Kompilator konwertuje ją na to:  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 Jeśli `flag` jest `false`, kompilator zgłasza wyjątek, zamiast przypisywać wartość -1 do `x`. W związku z tym aby uniknąć tego zachowania, poprawne kod używany jest następujący wiersz.  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` i `U` można przypisać typu Boolean, typ znakowy lub typu Liczba całkowita. Liczba całkowita typy mogą być podpisane lub unsigned i dowolnym rozmiarze z 8 bitów 64-bitowy.  
  
> [!NOTE]
>  Mimo że `SafeInt` klasy akceptuje dowolny rodzaj liczba całkowita, wykonuje wydajniej z typów bez znaku.  
  
 `E` błąd mechanizmu obsługi który `SafeInt` używa. Biblioteka SafeInt zostaną udostępnione dwa mechanizmy obsługi błędów. Domyślna zasada `SafeIntErrorPolicy_SafeIntException`, który zgłasza [safeintexception — klasa](../windows/safeintexception-class.md) wyjątek po wystąpieniu błędu. Inne zasady `SafeIntErrorPolicy_InvalidParameter`, który zatrzymuje program, jeśli wystąpi błąd.  
  
 Dostępne są dwie opcje, aby dostosować zasady błędów. Pierwsza opcja ma ustaw dla parametru `E` podczas tworzenia `SafeInt`. Użyj tej opcji, jeśli chcesz zmienić obsługi zasad dla co najmniej jeden błąd `SafeInt`. Inną możliwością jest określenie `_SAFEINT_DEFAULT_ERROR_POLICY` być dostosowane klasy obsługi błędów, przed wprowadzeniem `SafeInt` biblioteki. Użyj tej opcji, jeśli chcesz zmienić obsługi zasad dla wszystkich wystąpień błędów domyślne `SafeInt` klasy w kodzie.  
  
> [!NOTE]
>  Dostosowane klasy, która obsługuje błędy z Biblioteka SafeInt nie powinien zwrócić kontrolkę do kodu, który wywołuje program obsługi błędów. Po wywołaniu procedury obsługi błąd, wynik `SafeInt` operacji nie można zaufać.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [SafeIntException, klasa](../windows/safeintexception-class.md)