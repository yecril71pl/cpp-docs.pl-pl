---
title: Klasa CComCurrency
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 11463b7113876abdf0743b9f8c7df373fadd99ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497296"
---
# <a name="ccomcurrency-class"></a>Klasa CComCurrency

`CComCurrency`ma metody i operatory do tworzenia obiektu waluty i zarządzania nim.

## <a name="syntax"></a>Składnia

```
class CComCurrency
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor dla `CComCurrency` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Zwraca adres `m_currency` elementu członkowskiego danych.|
|[CComCurrency:: getułamek](#getfraction)|Wywołaj tę metodę, aby zwrócić składnik `CComCurrency` częściowy obiektu.|
|[CComCurrency:: GetInteger](#getinteger)|Wywołaj tę metodę, aby zwrócić składnik `CComCurrency` całkowity obiektu.|
|[CComCurrency:: Round](#round)|Wywołaj tę metodę, aby `CComCurrency` zaokrąglić obiekt do najbliższej wartości całkowitej.|
|[CComCurrency:: setułamek](#setfraction)|Wywołaj tę metodę, aby ustawić ułamek składnika `CComCurrency` obiektu.|
|[CComCurrency:: setinteger](#setinteger)|Wywołaj tę metodę, aby ustawić składnik `CComCurrency` Integer obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency:: operator-](#operator_-)|Ten operator służy do wykonywania odejmowania `CComCurrency` obiektu.|
|[CComCurrency:: operator! =](#operator_neq)|Porównuje `CComCurrency` dwa obiekty pod kątem nierówności.|
|[CComCurrency:: operator *](#operator_star)|Ten operator służy do wykonywania mnożenia w `CComCurrency` obiekcie.|
|[CComCurrency:: operator * =](#operator_star_eq)|Ten operator służy do wykonywania mnożenia `CComCurrency` obiektów i przypisywania wyniku.|
|[CComCurrency:: operator/](#operator_div)|Ten operator służy do wykonywania dzielenia na `CComCurrency` obiekt.|
|[CComCurrency:: operator/=](#operator_div_eq)|Ten operator służy do wykonywania dzielenia na `CComCurrency` obiekt i przypisywania go do wyniku.|
|[CComCurrency:: operator +](#operator_add)|Ten operator służy do wykonywania dodawania `CComCurrency` do obiektu.|
|[CComCurrency:: operator + =](#operator_add_eq)|Ten operator służy do wykonywania dodawania `CComCurrency` do obiektu i przypisywania wyniku do bieżącego obiektu.|
|[CComCurrency:: operator <](#operator_lt)|Ten operator porównuje `CComCurrency` dwa obiekty, aby określić, że są one mniejsze.|
|[CComCurrency:: operator < =](#operator_lt_eq)|Ten operator porównuje `CComCurrency` dwa obiekty, aby określić równość lub mniejszą.|
|[CComCurrency:: operator =](#operator_eq)|Ten operator przypisuje `CComCurrency` obiekt do nowej wartości.|
|[CComCurrency:: operator-=](#operator_-_eq)|Ten operator służy do wykonywania odejmowania `CComCurrency` obiektu i przypisywania go do wyniku.|
|[CComCurrency:: operator = =](#operator_eq_eq)|Ten operator porównuje `CComCurrency` dwa obiekty pod kątem równości.|
|[CComCurrency:: operator >](#operator_gt)|Ten operator porównuje `CComCurrency` dwa obiekty w celu określenia większego.|
|[CComCurrency:: operator > =](#operator_gt_eq)|Ten operator porównuje `CComCurrency` dwa obiekty, aby określić równość lub większą.|
|[CComCurrency:: operator — waluta](#operator_currency)|Rzutuje obiekt waluty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Zmienna waluty utworzona przez wystąpienie klasy.|

## <a name="remarks"></a>Uwagi

`CComCurrency`jest otoką dla typu danych Waluta. WALUTA jest implementowana jako 8-bajtowa liczba całkowita uzupełniająca, skalowana przez 10 000. Daje to stałą liczbę z 15 cyfr po lewej stronie przecinka dziesiętnego i 4 cyfry po prawej stronie. Typ danych WALUTowych jest niezwykle przydatny do obliczeń związanych z pieniędzmi lub w przypadku obliczeń mających stałe znaczenie.

`CComCurrency` Otoka implementuje operacje arytmetyczne, przypisywania i porównywania dla tego typu stałego. Obsługiwane aplikacje zostały wybrane do kontrolowania błędów zaokrąglania, które mogą wystąpić podczas obliczeń z ustalonym punktem.

`CComCurrency` Obiekt umożliwia dostęp do liczb znajdujących się po obu stronach przecinka dziesiętnego w postaci dwóch składników: składnika liczb całkowitych, który przechowuje wartość z lewej strony punktu dziesiętnego i składnik Ułamkowy, który przechowuje wartość z prawej strony punkt dziesiętny. Składnik Ułamkowy jest przechowywany wewnętrznie jako wartość całkowita z zakresu od-9999 (CY_MIN_FRACTION) do + 9999 (CY_MAX_FRACTION). Metoda [CComCurrency:: getułamek](#getfraction) zwraca wartość przeskalowana przez współczynnik 10000 (CY_SCALE).

Podczas określania wartości całkowitych i `CComCurrency` częściowych obiektu należy pamiętać, że składnik Ułamkowy jest liczbą z zakresu od 0 do 9999. Jest to ważne, gdy chodzi o użycie waluty, takiej jak Dolar amerykański, która wyraża kwoty, używając tylko dwóch cyfr znaczących po przecinku dziesiętnym. Mimo że ostatnie dwie cyfry nie są wyświetlane, muszą być brane pod uwagę.

|Wartość|Możliwe przypisania CComCurrency|
|-----------|---------------------------------------|
|$10.50|CComCurrency (10, 5000) *lub* CComCurrency (10.50)|
|$10.05|CComCurrency (10500) *lub* CComCurrency (10.05)|

Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są zdefiniowane w atlcur. h.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcur. h

##  <a name="ccomcurrency"></a>CComCurrency::CComCurrency

Konstruktor.

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>Parametry

*curSrc*<br/>
Istniejący `CComCurrency` obiekt.

*cySrc*<br/>
Zmienna typu CURRENCY.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Początkowa wartość nadana zmiennej `m_currency`członkowskiej.

*cSrc*<br/>
Znak zawierający początkową wartość podaną dla zmiennej `m_currency`składowej.

*nInteger*, *nFraction*<br/>
Całkowite i ułamkowe składniki początkowej wartości pieniężnej. Aby uzyskać więcej informacji, zobacz Omówienie [CComCurrency](../../atl/reference/ccomcurrency-class.md) .

*pDispSrc*<br/>
`IDispatch` Wskaźnik.

*varSrc*<br/>
Zmienna typu VARIANT. Ustawienia regionalne bieżącego wątku są używane do wykonania konwersji.

*szSrc*<br/>
Ciąg Unicode lub ANSI zawierający wartość początkową. Ustawienia regionalne bieżącego wątku są używane do wykonania konwersji.

### <a name="remarks"></a>Uwagi

Konstruktor ustawia początkową wartość [CComCurrency:: m_currency](#m_currency)i akceptuje szeroką gamę typów danych, w tym liczby całkowite, ciągi, liczby zmiennoprzecinkowe, zmienne walutowe i inne `CComCurrency` obiekty. Jeśli nie podano wartości, `m_currency` jest ustawiona na 0.

W przypadku błędu, takiego jak przepełnienie, konstruktory nie mają pustego wywołania `AtlThrow` specyfikacji wyjątku (**throw ()** ) z wynikiem HRESULT opisującym błąd.

W przypadku używania wartości zmiennoprzecinkowych lub podwójnych do przypisywania wartości, `CComCurrency(10.50)` należy pamiętać, `CComCurrency(10,5000)` że jest `CComCurrency(10,50)`ona odpowiednikiem i nie.

##  <a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Zwraca adres `m_currency` elementu członkowskiego danych.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres `m_currency` elementu członkowskiego danych

##  <a name="getfraction"></a>CComCurrency:: getułamek

Wywołaj tę metodę, aby zwrócić składnik `CComCurrency` częściowy obiektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik `m_currency` częściowy elementu członkowskiego danych.

### <a name="remarks"></a>Uwagi

Składnik Ułamkowy jest 4-cyfrową wartością całkowitą z zakresu od-9999 (CY_MIN_FRACTION) do + 9999 (CY_MAX_FRACTION). `GetFraction`zwraca tę wartość skalowanej przez 10000 (CY_SCALE). Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są zdefiniowane w atlcur. h.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>CComCurrency:: GetInteger

Wywołaj tę metodę, aby uzyskać składnik `CComCurrency` całkowity obiektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik `m_currency` Integer elementu członkowskiego danych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>CComCurrency::m_currency

Element członkowski danych waluty.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski zawiera walutę dostępną i manipulowaną przez metody tej klasy.

##  <a name="operator_-"></a>CComCurrency:: operator-

Ten operator służy do wykonywania odejmowania `CComCurrency` obiektu.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CComCurrency` Zwraca obiekt reprezentujący wynik odejmowania. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>CComCurrency:: operator! =

Ten operator porównuje dwa obiekty pod kątem nierówności.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Obiekt `CComCurrency` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element nie jest równy `CComCurrency` obiektowi; w przeciwnym razie, FAŁSZ.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>CComCurrency:: operator *

Ten operator służy do wykonywania mnożenia w `CComCurrency` obiekcie.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*cur*<br/>
`CComCurrency` Obiekt używany jako mnożnik.

### <a name="return-value"></a>Wartość zwracana

`CComCurrency` Zwraca obiekt reprezentujący wynik mnożenia. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>CComCurrency:: operator\*=

Ten operator służy do wykonywania mnożenia `CComCurrency` obiektów i przypisywania wyniku.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*cur*<br/>
`CComCurrency` Obiekt używany jako mnożnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>CComCurrency:: operator/

Ten operator służy do wykonywania dzielenia na `CComCurrency` obiekt.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

`CComCurrency` Zwraca obiekt reprezentujący wynik dzielenia. Jeśli dzielnik ma wartość 0, wystąpi błąd potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>CComCurrency:: operator/=

Ten operator służy do wykonywania dzielenia na `CComCurrency` obiekt i przypisywania go do wyniku.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. Jeśli dzielnik ma wartość 0, wystąpi błąd potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>CComCurrency:: operator +

Ten operator służy do wykonywania dodawania `CComCurrency` do obiektu.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiekt, który ma zostać dodany do oryginalnego obiektu.

### <a name="return-value"></a>Wartość zwracana

`CComCurrency` Zwraca obiekt reprezentujący wynik dodania. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>CComCurrency:: operator + =

Ten operator służy do wykonywania dodawania `CComCurrency` do obiektu i przypisywania wyniku do bieżącego obiektu.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiekt.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>CComCurrency:: operator&lt;

Ten operator porównuje `CComCurrency` dwa obiekty, aby określić, że są one mniejsze.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy niż drugi, w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>CComCurrency:: operator&lt;=

Ten operator porównuje `CComCurrency` dwa obiekty, aby określić równość lub mniejszą.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy lub równy drugiemu, FAŁSZ w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>CComCurrency:: operator =

Ten operator przypisuje `CComCurrency` obiekt do nowej wartości.

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>Parametry

*curSrc*<br/>
Element `CComCurrency` obiektu.

*cySrc*<br/>
Zmienna typu CURRENCY.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Wartość liczbowa, która ma zostać `CComCurrency` przypisana do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>CComCurrency:: operator-=

Ten operator służy do wykonywania odejmowania `CComCurrency` obiektu i przypisywania go do wyniku.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, ten operator wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>CComCurrency:: operator = =

Ten operator porównuje `CComCurrency` dwa obiekty pod kątem równości.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli obiekty są równe (oznacza to, `m_currency` że elementy członkowskie danych, zarówno liczba całkowita, jak i ułamek, w obu obiektach mają tę samą wartość), w przeciwnym razie false.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>CComCurrency:: operator&gt;

Ten operator porównuje `CComCurrency` dwa obiekty w celu określenia większego.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy niż drugi, w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>CComCurrency:: operator&gt;=

Ten operator porównuje `CComCurrency` dwa obiekty, aby określić równość lub większą.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy lub równy drugiemu, FAŁSZ w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>CComCurrency:: operator — waluta

Operatory te służą do rzutowania `CComCurrency` obiektu na typ danych walutowych.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do obiektu waluty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>CComCurrency:: Round

Wywołaj tę metodę, aby zaokrąglić walutę do określonej liczby miejsc dziesiętnych.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecimals*<br/>
Liczba cyfr, do których `m_currency` zostanie zaokrąglona, z zakresu od 0 do 4.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>CComCurrency:: setułamek

Wywołaj tę metodę, aby ustawić ułamek składnika `CComCurrency` obiektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nFraction*<br/>
Wartość, która ma zostać przypisana do części `m_currency` ułamkowej elementu członkowskiego danych. Znak części ułamkowej musi być taki sam jak składnik Integer, a wartość musi należeć do zakresu od-9999 (CY_MIN_FRACTION) do + 9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>CComCurrency:: setinteger

Wywołaj tę metodę, aby ustawić składnik `CComCurrency` Integer obiektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Wartość, która ma zostać przypisana do składnika `m_currency` Integer elementu członkowskiego danych. Znak składnika Integer musi być zgodny ze znakiem istniejącego składnika ułamkowego.

*nInteger* musi należeć do zakresu od CY_MIN_INTEGER do CY_MAX_INTEGER włącznie. Te wartości są zdefiniowane w atlcur. h.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa COleCurrency](../../mfc/reference/colecurrency-class.md)<br/>
[WALUTOWY](/windows/win32/api/wtypes/ns-wtypes-cy)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
