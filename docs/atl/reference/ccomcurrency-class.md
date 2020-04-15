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
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327943"
---
# <a name="ccomcurrency-class"></a>Klasa CComCurrency

`CComCurrency`posiada metody i operatory do tworzenia i zarządzania obiektem CURRENCY.

## <a name="syntax"></a>Składnia

```
class CComCurrency
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor `CComCurrency` dla obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Zwraca adres członka `m_currency` danych.|
|[CComCurrency::GetFraction](#getfraction)|Wywołanie tej metody, aby zwrócić `CComCurrency` składnik ułamkowy obiektu.|
|[CComCurrency::GetInteger](#getinteger)|Wywołanie tej metody, aby zwrócić `CComCurrency` składnik liczby całkowitej obiektu.|
|[CComCurrency::Okrągły](#round)|Wywołanie tej metody, aby zaokrąglić `CComCurrency` obiekt do najbliższej wartości całkowitej.|
|[CComCurrency::SetFraction](#setfraction)|Wywołanie tej metody, aby ustawić `CComCurrency` składnik ułamkowy obiektu.|
|[CComCurrency::SetInteger](#setinteger)|Wywołanie tej metody, aby ustawić `CComCurrency` składnik liczby całkowitej obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::operator -](#operator_-)|Ten operator jest używany do odejmowania obiektu. `CComCurrency`|
|[CComCurrency::operator !=](#operator_neq)|Porównuje dwa `CComCurrency` obiekty dla nierówności.|
|[CComCurrency::operator *](#operator_star)|Ten operator jest używany do wykonywania `CComCurrency` mnożenia na obiekcie.|
|[CComCurrency::operator *=](#operator_star_eq)|Ten operator jest używany do wykonywania `CComCurrency` mnożenia na obiekcie i przypisać mu wynik.|
|[CComCurrency::operator /](#operator_div)|Ten operator jest używany do `CComCurrency` wykonywania podziału na obiekcie.|
|[CComCurrency::operator /=](#operator_div_eq)|Ten operator jest używany do `CComCurrency` wykonywania podziału na obiekcie i przypisać mu wynik.|
|[CComCurrency::operator +](#operator_add)|Ten operator jest używany do `CComCurrency` wykonywania dodawania na obiekcie.|
|[CComCurrency::operator +=](#operator_add_eq)|Ten operator jest używany do `CComCurrency` dodawania obiektu i przypisywania wyniku do bieżącego obiektu.|
|[CComCurrency::operator <](#operator_lt)|Ten operator porównuje `CComCurrency` dwa obiekty, aby określić mniejsze.|
|[CComCurrency::operator <=](#operator_lt_eq)|Ten operator porównuje `CComCurrency` dwa obiekty do określenia równości lub mniejsze.|
|[CComCurrency::operator =](#operator_eq)|Ten operator przypisuje `CComCurrency` obiekt do nowej wartości.|
|[CComCurrency::operator -=](#operator_-_eq)|Ten operator jest używany do wykonywania `CComCurrency` odejmowania na obiekcie i przypisać mu wynik.|
|[CComCurrency::operator ==](#operator_eq_eq)|Ten operator porównuje `CComCurrency` dwa obiekty dla równości.|
|[CComCurrency::operator >](#operator_gt)|Ten operator porównuje `CComCurrency` dwa obiekty, aby określić większe.|
|[CComCurrency::operator >=](#operator_gt_eq)|Ten operator porównuje `CComCurrency` dwa obiekty do określenia równości lub większe.|
|[CComCurrency::operator WALUTA](#operator_currency)|Rzutuje obiekt CURRENCY.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Zmienna WALUTA utworzona przez wystąpienie klasy.|

## <a name="remarks"></a>Uwagi

`CComCurrency`jest otoką dla typu danych CURRENCY. WALUTA jest implementowana jako 8-bajtowa wartość całkowita z dopełnieniem 2000 skalowana przez 10 000. Daje to stały numer punktowy z 15 cyframi po lewej stronie przecinka dziesiętnego i 4 cyframi po prawej stronie. Typ danych CURRENCY jest niezwykle przydatny w obliczeniach dotyczących pieniądza lub w obliczeniach o stałym punkcie, w których dokładność jest ważna.

Otoka `CComCurrency` implementuje operacje arytmetyczne, przypisania i porównania dla tego typu stałego punktu. Obsługiwane aplikacje zostały wybrane do kontrolowania błędów zaokrąglania, które mogą wystąpić podczas obliczeń stałych punktów.

Obiekt `CComCurrency` zapewnia dostęp do liczb po obu stronach przecinka dziesiętnego w postaci dwóch składników: składnika liczby całkowitej, który przechowuje wartość po lewej stronie przecinka dziesiętnego oraz składnika ułamkowego, który przechowuje wartość po prawej stronie przecinka dziesiętnego. Składnik ułamkowy jest przechowywany wewnętrznie jako wartość całkowita między -9999 (CY_MIN_FRACTION) i +9999 (CY_MAX_FRACTION). Metoda [CComCurrency::GetFraction](#getfraction) zwraca wartość skalowana przez współczynnik 10000 (CY_SCALE).

Określając składniki całkowite i ułamkowe `CComCurrency` obiektu, należy pamiętać, że składnik ułamkowy jest liczbą w zakresie od 0 do 9999. Jest to ważne w przypadku waluty, takiej jak dolar amerykański, która wyraża kwoty przy użyciu tylko dwóch cyfr znaczących po przecinku dziesiętnym. Mimo że dwie ostatnie cyfry nie są wyświetlane, należy je wziąć pod uwagę.

|Wartość|Możliwe przypisania CComCurrency|
|-----------|---------------------------------------|
|zł.|CComCurrency(10,5000) *lub* CComCurrency(10.50)|
|zł.|CComCurrency(10,500) *lub* CComCurrency(10.05)|

Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są zdefiniowane w pliku atlcur.h.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CComCurrency::CComCurrency

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

*curSrc ( curSrc )*<br/>
Istniejący `CComCurrency` obiekt.

*cysrc (cysrc)*<br/>
Zmienna typu WALUTA.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Wartość początkowa podana `m_currency`zmiennej członkowskiej .

*Csrc*<br/>
Znak zawierający wartość początkową podana `m_currency`zmiennej członkowskiej .

*nInteger*, *nFraction*<br/>
Składniki całkowite i ułamkowe początkowej wartości pieniężnej. Zobacz [przegląd CComCurrency,](../../atl/reference/ccomcurrency-class.md) aby uzyskać więcej informacji.

*pDispSrc (Niedłumice stronicowanie)*<br/>
Wskaźnik. `IDispatch`

*varSrc ( varSrc )*<br/>
Zmienna typu VARIANT. Ustawienia regionalne bieżącego wątku jest używany do wykonywania konwersji.

*szsrc ( szsrc )*<br/>
Ciąg Unicode lub ANSI zawierający wartość początkową. Ustawienia regionalne bieżącego wątku jest używany do wykonywania konwersji.

### <a name="remarks"></a>Uwagi

Konstruktor ustawia wartość początkową [CComCurrency::m_currency](#m_currency)i akceptuje szeroki zakres typów danych, w tym liczby całkowite, ciągi, liczby zmienne `CComCurrency` zmienne, zmienne WALUTOWE i inne obiekty. Jeśli nie podano `m_currency` żadnej wartości, jest ustawiona na 0.

W przypadku błędu, takiego jak przepełnienie, konstruktorów brak pustej specyfikacji wyjątku **(throw()**) wywołać `AtlThrow` z HRESULT opisujące błąd.

W przypadku przypisywania wartości zmiennoprzecinkowej `CComCurrency(10.50)` lub `CComCurrency(10,5000)` podwójnej `CComCurrency(10,50)`przy użyciu wartości zmiennoprzecinkowych lub podwójnych należy pamiętać, że jest ona równoważna wartości, a nie .

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Zwraca adres członka `m_currency` danych.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres elementu `m_currency` członkowskiego danych

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CComCurrency::GetFraction

Wywołanie tej metody, aby zwrócić `CComCurrency` składnik ułamkowy obiektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik ułamkowy `m_currency` elementu członkowskiego danych.

### <a name="remarks"></a>Uwagi

Składnik ułamkowy jest 4-cyfrową wartością całkowitą między -9999 (CY_MIN_FRACTION) i +9999 (CY_MAX_FRACTION). `GetFraction`zwraca tę wartość skalowane przez 10000 (CY_SCALE). Wartości CY_MIN_FRACTION, CY_MAX_FRACTION i CY_SCALE są zdefiniowane w pliku atlcur.h.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency::GetInteger

Wywołanie tej metody, aby uzyskać `CComCurrency` składnik liczby całkowitej obiektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik liczby całkowitej `m_currency` elementu członkowskiego danych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CComCurrency::m_currency

Element członkowski danych WALUTY.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski przechowuje waluty dostępne i manipulowane przez metody tej klasy.

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency::operator -

Ten operator jest używany do odejmowania obiektu. `CComCurrency`

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik odejmowania. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency::operator !=

Ten operator porównuje dwa obiekty dla nierówności.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CComCurrency` element nie jest równy obiektowi; w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency::operator *

Ten operator jest używany do wykonywania `CComCurrency` mnożenia na obiekcie.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*Cur*<br/>
Obiekt `CComCurrency` używany jako mnożnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik mnożenia. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency::operator\*=

Ten operator jest używany do wykonywania `CComCurrency` mnożenia na obiekcie i przypisać mu wynik.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Mnożnik.

*Cur*<br/>
Obiekt `CComCurrency` używany jako mnożnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency::operator /

Ten operator jest używany do `CComCurrency` wykonywania podziału na obiekcie.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik podziału. Jeśli dzielnik jest 0, wystąpi błąd potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency::operator /=

Ten operator jest używany do `CComCurrency` wykonywania podziału na obiekcie i przypisać mu wynik.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dzielnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. Jeśli dzielnik jest 0, wystąpi błąd potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency::operator +

Ten operator jest używany do `CComCurrency` wykonywania dodawania na obiekcie.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt, `CComCurrency` który ma zostać dodany do oryginalnego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CComCurrency` obiekt reprezentujący wynik dodania. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency::operator +=

Ten operator jest używany do `CComCurrency` dodawania obiektu i przypisywania wyniku do bieżącego obiektu.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency::operator&lt;

Ten operator porównuje `CComCurrency` dwa obiekty, aby określić mniejsze.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy niż drugi, w przeciwnym razie wartość FAŁSZ.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency::operator&lt;=

Ten operator porównuje `CComCurrency` dwa obiekty do określenia równości lub mniejsze.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy lub równy drugiemu, wartość FAŁsz w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency::operator =

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

*curSrc ( curSrc )*<br/>
Obiekt `CComCurrency`.

*cysrc (cysrc)*<br/>
Zmienna typu WALUTA.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Wartość liczbowa do przypisania do `CComCurrency` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency::operator -=

Ten operator jest używany do wykonywania `CComCurrency` odejmowania na obiekcie i przypisać mu wynik.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComCurrency` obiekt. W przypadku błędu, takiego jak przepełnienie, `AtlThrow` ten operator wywołuje z HRESULT opisujące błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency::operator ==

Ten operator porównuje `CComCurrency` dwa obiekty dla równości.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są `m_currency` równe (czyli elementy członkowskie danych, zarówno liczby całkowitej, jak i ułamkowe, w obu obiektach mają tę samą wartość), WARTOŚĆ FAŁSZ W przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency::operator&gt;

Ten operator porównuje `CComCurrency` dwa obiekty, aby określić większe.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż drugi, w przeciwnym razie wartość FAŁSZ.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency::operator&gt;=

Ten operator porównuje `CComCurrency` dwa obiekty do określenia równości lub większe.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Cur*<br/>
Obiekt `CComCurrency`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy lub równy drugiemu, WARTOŚĆ FAŁSZ W przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency::operator WALUTA

Te operatory są `CComCurrency` używane do rzutu obiektu na typ danych CURRENCY.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do obiektu CURRENCY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CComCurrency::Okrągły

Wywołanie tej metody, aby zaokrąglić walutę do określonej liczby miejsc dziesiętnych.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecymals*<br/>
Liczba cyfr, do `m_currency` których zostanie zaokrąglona, w zakresie od 0 do 4.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CComCurrency::SetFraction

Wywołanie tej metody, aby ustawić `CComCurrency` składnik ułamkowy obiektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nFraction (nFraction)*<br/>
Wartość, która ma być przypisana do `m_currency` składnika ułamkowego elementu członkowskiego danych. Znak składnika ułamkowego musi być taki sam jak składnik liczby całkowitej, a wartość musi znajdować się w zakresie od -9999 (CY_MIN_FRACTION) do +9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency::SetInteger

Wywołanie tej metody, aby ustawić `CComCurrency` składnik liczby całkowitej obiektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Wartość, która ma być przypisana do `m_currency` składnika liczby całkowitej elementu członkowskiego danych. Znak składnika liczby całkowitej musi być zgodny ze znakiem istniejącego składnika ułamkowego.

*nInteger* musi znajdować się w zakresie CY_MIN_INTEGER CY_MAX_INTEGER włącznie. Wartości te są zdefiniowane w pliku atlcur.h.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa COleCurrency](../../mfc/reference/colecurrency-class.md)<br/>
[Waluty](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
