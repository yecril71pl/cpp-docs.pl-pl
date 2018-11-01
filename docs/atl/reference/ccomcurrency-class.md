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
ms.openlocfilehash: 5a619eef33a60dc1a34d31c3d51614de20fc8f28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451159"
---
# <a name="ccomcurrency-class"></a>Klasa CComCurrency

`CComCurrency` zawiera metody i operatorów do tworzenia i zarządzania obiektem waluty.

## <a name="syntax"></a>Składnia

```
class CComCurrency
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor `CComCurrency` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Zwraca adres `m_currency` element członkowski danych.|
|[CComCurrency::GetFraction](#getfraction)|Wywołanie tej metody, aby zwrócić ułamkową część `CComCurrency` obiektu.|
|[CComCurrency::GetInteger](#getinteger)|Wywołanie tej metody zwrócić składowej całkowitą `CComCurrency` obiektu.|
|[CComCurrency::Round](#round)|Wywołaj tę metodę, aby zaokrąglić `CComCurrency` obiektu do najbliższej wartości całkowitej.|
|[CComCurrency::SetFraction](#setfraction)|Wywołanie tej metody, aby ustawić ułamkową część `CComCurrency` obiektu.|
|[CComCurrency::SetInteger](#setinteger)|Wywołanie tej metody można ustawić liczby całkowitej składowej `CComCurrency` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::operator-](#operator_-)|Ten operator jest używany do przeprowadzania odejmowania `CComCurrency` obiektu.|
|[CComCurrency::operator! =](#operator_neq)|Porównuje dwa `CComCurrency` obiekty pod kątem nierówności.|
|[CComCurrency::operator *](#operator_star)|Ten operator jest używany do przeprowadzania mnożenia `CComCurrency` obiektu.|
|[CComCurrency::operator * =](#operator_star_eq)|Ten operator jest używany do przeprowadzania mnożenia `CComCurrency` obiektu i przypisać jej wynik.|
|[CComCurrency::operator /](#operator_div)|Ten operator jest używany do wykonywania dzielenia na `CComCurrency` obiektu.|
|[CComCurrency::operator / =](#operator_div_eq)|Ten operator jest używany do wykonywania dzielenia na `CComCurrency` obiektu i przypisać jej wynik.|
|[CComCurrency::operator +](#operator_add)|Ten operator jest używany podczas dodawania `CComCurrency` obiektu.|
|[CComCurrency::operator +=](#operator_add_eq)|Ten operator jest używany podczas dodawania `CComCurrency` obiektu i przypisz wynik do bieżącego obiektu.|
|[CComCurrency::operator <](#operator_lt)|Ten operator porównuje dwa `CComCurrency` obiektów, aby określić mniejszy.|
|[CComCurrency::operator < =](#operator_lt_eq)|Ten operator porównuje dwa `CComCurrency` obiektów, aby określić równości lub mniejszy.|
|[CComCurrency::operator =](#operator_eq)|Przypisuje ten operator `CComCurrency` obiektu nową wartość.|
|[CComCurrency::operator-=](#operator_-_eq)|Ten operator jest używany do przeprowadzania odejmowania `CComCurrency` obiektu i przypisać jej wynik.|
|[CComCurrency::operator ==](#operator_eq_eq)|Ten operator porównuje dwa `CComCurrency` obiekty pod kątem równości.|
|[CComCurrency::operator >](#operator_gt)|Ten operator porównuje dwa `CComCurrency` obiektów, aby określić wyższy.|
|[CComCurrency::operator > =](#operator_gt_eq)|Ten operator porównuje dwa `CComCurrency` obiektów, aby określić równości lub większy.|
|[CComCurrency::operator waluty](#operator_currency)|Rzutuje obiektu waluty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Zmienna waluty, utworzone przez wystąpienie klasy.|

## <a name="remarks"></a>Uwagi

`CComCurrency` jest otoką elementu dla typu danych walutowych. WALUTA jest implementowany jako uzupełnienia do dwóch 8-bajtową wartość całkowitą skalowania przez 10 000. Dzięki temu stałoprzecinkowa liczba z 15 cyfr z lewej strony punktu dziesiętnego i 4 cyfr po prawej stronie. Typ danych walutowych jest niezwykle przydatna funkcja dla obliczeń walutowych lub wszelkie stałoprzecinkowe obliczenia, których dokładności jest ważna.

`CComCurrency` Otoki implementuje operacje arytmetyczne, przypisywania i porównania dla tego typu stałoprzecinkowa. Obsługiwane aplikacje zostały wybrane do kontrolowania błędy zaokrągleń, które mogą wystąpić podczas obliczeń stałoprzecinkowego.

`CComCurrency` Obiekt umożliwia dostęp do numerów na dowolnej stronie przecinka dziesiętnego w postaci dwóch składników: składnika całkowitego, który przechowuje wartość z lewej strony punktu dziesiętnego i ułamkowych składnik, który przechowuje wartość po prawej stronie punkt dziesiętny. Części ułamkowe są przechowywane wewnętrznie jako wartość całkowita z przedziału-9999 (CY_MIN_FRACTION) i +9999 (CY_MAX_FRACTION). Metoda [CComCurrency::GetFraction](#getfraction) zwraca wartość skalowania przez współczynnik 10000 (CY_SCALE).

Podczas określania liczby całkowitej i ułamkowych części `CComCurrency` obiektów, pamiętaj, że składnik ułamkowe ma liczba z zakresu od 0 do 9999. Jest to ważne podczas pracy z waluty przykład w dolarach amerykańskich, który wyraża kwoty przy użyciu tylko dwie cyfry znaczące, po punkcie dziesiętnym. Mimo że nie są wyświetlane dwie ostatnie cyfry, muszą one zostać pobrane do konta.

|Wartość|Możliwe przypisania CComCurrency|
|-----------|---------------------------------------|
|$10.50|CComCurrency(10,5000) *lub* CComCurrency(10.50)|
|$10.05|CComCurrency(10,500) *lub* CComCurrency(10.05)|

Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są definiowane w atlcur.h.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcur.h

##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency

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
Istniejące `CComCurrency` obiektu.

*cySrc*<br/>
Zmienna typu waluty.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Początkowa wartość do zmiennej elementu członkowskiego `m_currency`.

*cSrc*<br/>
Znak zawierający początkowa wartość do zmiennej elementu członkowskiego `m_currency`.

*nInteger*, *nFraction*<br/>
Liczba całkowita i ułamkowych części wartość pieniężną. Zobacz [CComCurrency](../../atl/reference/ccomcurrency-class.md) Przegląd, aby uzyskać więcej informacji.

*pDispSrc*<br/>
`IDispatch` Wskaźnika.

*varSrc*<br/>
Zmienna typu VARIANT. Ustawienia regionalne bieżącego wątku jest używany do wykonywania konwersji.

*szSrc*<br/>
Ciąg Unicode lub ANSI, zawierający wartość początkową. Ustawienia regionalne bieżącego wątku jest używany do wykonywania konwersji.

### <a name="remarks"></a>Uwagi

Konstruktor ustawia wartość początkową [CComCurrency::m_currency](#m_currency)i akceptuje szeroką gamę typów danych, w tym liczb całkowitych, ciągów, liczb zmiennoprzecinkowych, waluty, zmienne i inne `CComCurrency` obiektów. Jeśli wartość nie zostanie podany, `m_currency` jest równa 0.

W przypadku wystąpienia błędu, takie jak przepełnienie konstruktorów, zawiera specyfikację wyjątku pusty (**throw()**) wywołanie `AtlThrow` z opisem błędu HRESULT.

Korzystając z wartości zmiennoprzecinkowe i podwójne do przypisania wartości, należy pamiętać, że `CComCurrency(10.50)` jest odpowiednikiem `CComCurrency(10,5000)` i nie `CComCurrency(10,50)`.

##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr

Zwraca adres `m_currency` element członkowski danych.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres `m_currency` element członkowski danych

##  <a name="getfraction"></a>  CComCurrency::GetFraction

Wywołanie tej metody, aby zwrócić ułamkową część `CComCurrency` obiektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca część ułamkową `m_currency` element członkowski danych.

### <a name="remarks"></a>Uwagi

Części ułamkowe jest 4-cyfrowego całkowitą z zakresu od-9999 (CY_MIN_FRACTION) i +9999 (CY_MAX_FRACTION). `GetFraction` zwraca tę wartość skalowania przez 10000 (CY_SCALE). Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są definiowane w atlcur.h.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>  CComCurrency::GetInteger

Wywołanie tej metody można pobrać liczby całkowitej składowej `CComCurrency` obiektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca część całkowitą `m_currency` element członkowski danych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>  CComCurrency::m_currency

Element członkowski danych waluty.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski przechowuje waluty dostępne i manipulować metody tej klasy.

##  <a name="operator_-"></a>  CComCurrency::operator-

Ten operator jest używany do przeprowadzania odejmowania `CComCurrency` obiektu.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik odejmowania. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>  CComCurrency::operator! =

Ten operator porównuje dwa obiekty pod kątem nierówności.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany nie jest równa `CComCurrency` obiektu; w przeciwnym razie wartość FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>  CComCurrency::operator *

Ten operator jest używany do przeprowadzania mnożenia `CComCurrency` obiektu.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*cur*<br/>
`CComCurrency` Używana jako mnożnik obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik mnożenia. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>  CComCurrency::operator \*=

Ten operator jest używany do przeprowadzania mnożenia `CComCurrency` obiektu i przypisać jej wynik.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*cur*<br/>
`CComCurrency` Używana jako mnożnik obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>  CComCurrency::operator /

Ten operator jest używany do wykonywania dzielenia na `CComCurrency` obiektu.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiektów reprezentująca wynik dzielenia. Jeśli dzielnik jest 0, wystąpi błąd asercji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>  CComCurrency::operator / =

Ten operator jest używany do wykonywania dzielenia na `CComCurrency` obiektu i przypisać jej wynik.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiektu. Jeśli dzielnik jest 0, wystąpi błąd asercji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>  CComCurrency::operator +

Ten operator jest używany podczas dodawania `CComCurrency` obiektu.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiektów, które mają zostać dodane do oryginalnego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik dodawania. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>  CComCurrency::operator +=

Ten operator jest używany podczas dodawania `CComCurrency` obiektu i przypisz wynik do bieżącego obiektu.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>  CComCurrency::operator &lt;

Ten operator porównuje dwa `CComCurrency` obiektów, aby określić mniejszy.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy od drugiego, wartość FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>  CComCurrency::operator &lt;=

Ten operator porównuje dwa `CComCurrency` obiektów, aby określić równości lub mniejszy.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy niż lub równe drugiemu, wartość FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>  CComCurrency::operator =

Przypisuje ten operator `CComCurrency` obiektu nową wartość.

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
Zmienna typu waluty.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc* , *ulSrc*, *dSrc*<br/>
Wartość liczbowa do przypisania do `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>  CComCurrency::operator-=

Ten operator jest używany do przeprowadzania odejmowania `CComCurrency` obiektu i przypisać jej wynik.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienie wywołuje ten operator `AtlThrow` z opisem błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>  CComCurrency::operator ==

Ten operator porównuje dwa `CComCurrency` obiekty pod kątem równości.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
`CComCurrency` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe (oznacza to, `m_currency` składowe danych, zarówno integer i ułamkowych, zarówno w obiekty mają taką samą wartość), wartość FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>  CComCurrency::operator &gt;

Ten operator porównuje dwa `CComCurrency` obiektów, aby określić wyższy.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy od drugiego, wartość FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>  CComCurrency::operator &gt;=

Ten operator porównuje dwa `CComCurrency` obiektów, aby określić równości lub większy.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*cur*<br/>
Element `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy lub równy drugiemu FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>  CComCurrency::operator waluty

Te operatory są używane do rzutowania `CComCurrency` obiektu na typ danych walutowych.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do obiektu waluty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>  CComCurrency::Round

Wywołaj tę metodę, aby zaokrąglić walucie określonej liczby miejsc po przecinku.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecimals*<br/>
Liczba cyfr, do którego `m_currency` zostanie zaokrąglony z zakresu od 0 do 4.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>  CComCurrency::SetFraction

Wywołanie tej metody, aby ustawić ułamkową część `CComCurrency` obiektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nFraction*<br/>
Wartość do przypisania do składnika ułamkowe `m_currency` element członkowski danych. Znak ułamkowych części musi taka sama jak składnika całkowitego, a wartość musi należeć do zakresu-9999 (CY_MIN_FRACTION) do +9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>  CComCurrency::SetInteger

Wywołanie tej metody można ustawić liczby całkowitej składowej `CComCurrency` obiektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Wartość do przypisania do liczby całkowitej składowej `m_currency` element członkowski danych. Znak składnika całkowitego musi odpowiadać znak istniejący składnik ułamkowe.

*nInteger* musi należeć do zakresu CY_MIN_INTEGER do CY_MAX_INTEGER (włącznie). Te wartości są definiowane w atlcur.h.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa COleCurrency](../../mfc/reference/colecurrency-class.md)<br/>
[WALUTY](/windows/desktop/api/wtypes/ns-wtypes-tagcy)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
