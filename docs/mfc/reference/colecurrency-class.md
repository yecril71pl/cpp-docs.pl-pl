---
title: Klasa COleCurrency
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: ced4554701cef5fd6f790b9e37f4c1b41746b1ad
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470969"
---
# <a name="colecurrency-class"></a>Klasa COleCurrency

Hermetyzuje `CURRENCY` Typ danych automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleCurrency
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Konstruuje `COleCurrency` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleCurrency:: format](#format)|Generuje sformatowaną reprezentację obiektu w postaci ciągu `COleCurrency` .|
|[COleCurrency:: GetStatus](#getstatus)|Pobiera stan (ważność) tego `COleCurrency` obiektu.|
|[COleCurrency::P arseCurrency](#parsecurrency)|Odczytuje wartość waluty z ciągu i ustawia wartość `COleCurrency` .|
|[COleCurrency:: SetCurrency](#setcurrency)|Ustawia wartość tego `COleCurrency` obiektu.|
|[COleCurrency:: SetStatus](#setstatus)|Ustawia stan (ważność) dla tego `COleCurrency` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje `COleCurrency` wartość.|
|[operator +,-](#operator_plus_minus)|Dodaje, odejmuje i zmienia znak `COleCurrency` wartości.|
|[operator + =,-=](#operator_plus_minus_eq)|Dodaje i odejmuje `COleCurrency` wartość z tego `COleCurrency` obiektu.|
|[operator */](#operator_star)|Skaluje `COleCurrency` wartość przez wartość całkowitą.|
|[operator * =,/=](#operator_star_div_eq)|Skaluje tę `COleCurrency` wartość przez wartość całkowitą.|
|[ <<operatora](#operator_stream)|Wyprowadza `COleCurrency` wartość do `CArchive` lub `CDumpContext` .|
|[ >>operatora](#operator_stream)|Wprowadza `COleCurrency` obiekt z `CArchive` .|
|[Waluta operatora](#operator_currency)|Konwertuje `COleCurrency` wartość na walutę.|
|[operator = =, <, <= itd.](#colecurrency_relational_operators)|Porównuje dwie `COleCurrency` wartości.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|Zawiera WALUTę podstawową dla tego `COleCurrency` obiektu.|
|[COleCurrency:: m_status](#m_status)|Zawiera stan tego `COleCurrency` obiektu.|

## <a name="remarks"></a>Uwagi

`COleCurrency`nie ma klasy bazowej.

WALUTA jest zaimplementowana jako 8-bajtowa, dwie wartości całkowite do uzupełnienia, skalowane przez 10 000. Daje to stałą liczbę z 15 cyfr po lewej stronie przecinka dziesiętnego i 4 cyfry po prawej stronie. Typ danych WALUTowych jest niezwykle przydatny do obliczeń związanych z pieniędzmi lub w przypadku obliczeń o stałej liczbie, w których dokładność jest ważna. Jest to jeden z możliwych typów dla `VARIANT` typu danych automatyzacji OLE.

`COleCurrency`implementuje także podstawowe operacje arytmetyczne dla tego typu stałego. Zostały wybrane obsługiwane operacje w celu kontrolowania błędów zaokrąglania występujących podczas obliczeń z ustalonym punktem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleCurrency`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

Konstruuje `COleCurrency` obiekt.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*cySrc*<br/>
Wartość waluty, która ma zostać skopiowana do nowego `COleCurrency` obiektu.

*curSrc*<br/>
Istniejący `COleCurrency` obiekt do skopiowania do nowego `COleCurrency` obiektu.

*varSrc*<br/>
Istniejąca `VARIANT` Struktura danych (prawdopodobnie `COleVariant` obiekt) do przekonwertowania na wartość walutową (VT_CY) i skopiowana do nowego `COleCurrency` obiektu.

*nUnits*, *nFractionalUnits* wskazują jednostki i część ułamkową (w 1/10000) wartości, która ma zostać skopiowana do nowego `COleCurrency` obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleCurrency` obiekty zainicjowane do określonej wartości. Poniżej znajduje się krótki opis każdego z tych konstruktorów. O ile nie zaznaczono inaczej, stan nowego `COleCurrency` elementu jest ustawiony na wartość prawidłowy.

- COleCurrency () konstruuje `COleCurrency` obiekt zainicjowany do 0 (zero).

- COleCurrency ( `cySrc` ) konstruuje `COleCurrency` obiekt z wartości [walutowej](/windows/win32/api/wtypes/ns-wtypes-cy-r1) .

- COleCurrency ( `curSrc` ) konstruuje `COleCurrency` obiekt z istniejącego `COleCurrency` obiektu. Nowy obiekt ma ten sam stan co obiekt źródłowy.

- COleCurrency ( `varSrc` ) konstruuje `COleCurrency` obiekt. Próbuje skonwertować strukturę [wariantu](/windows/win32/api/oaidl/ns-oaidl-variant) lub `COleVariant` obiekt na wartość walutową (VT_CY). Jeśli ta konwersja zakończyła się pomyślnie, przekonwertowana wartość jest kopiowana do nowego `COleCurrency` obiektu. Jeśli tak nie jest, wartość `COleCurrency` obiektu jest równa zero (0), a jego stan jest nieprawidłowy.

- COleCurrency ( `nUnits` , `nFractionalUnits` ) konstruuje `COleCurrency` obiekt z określonych składników liczbowych. Jeśli wartość bezwzględna części ułamkowej jest większa niż 10 000, odpowiednie dostosowanie jest dokonywane w jednostkach. Należy zauważyć, że jednostki i części ułamkowe są określone przez podpisane długie wartości.

Aby uzyskać więcej informacji, zobacz wartości [walutowe](/windows/win32/api/wtypes/ns-wtypes-cy-r1) i [wariantowe](/windows/win32/api/oaidl/ns-oaidl-variant) w Windows SDK.

### <a name="example"></a>Przykład

Poniższe przykłady przedstawiają efekty konstruktorów z parametrem zero i dwoma parametrami:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency:: format

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć sformatowaną reprezentację wartości walutowej.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Wskazuje flagi dla ustawień regionalnych. Tylko następująca flaga dotyczy waluty:

- LOCALE_NOUSEROVERRIDE Użyj domyślnych ustawień regionalnych systemu zamiast niestandardowych ustawień użytkownika.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych do użycia podczas konwersji.

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera sformatowaną wartość waluty.

### <a name="remarks"></a>Uwagi

Wartość ta jest formatowana przy użyciu lokalnych specyfikacji języka (identyfikatorów ustawień regionalnych). Symbol waluty nie jest uwzględniony w zwracanej wartości. Jeśli stan tego `COleCurrency` obiektu ma wartość null, zwracana wartość jest ciągiem pustym. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określany przez zasób ciągu IDS_INVALID_CURRENCY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency:: GetStatus

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać stan (ważność) danego `COleCurrency` obiektu.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan tej `COleCurrency` wartości.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowana przez `CurrencyStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że ten `COleCurrency` obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że ten `COleCurrency` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że ten `COleCurrency` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleCurrency` obiektu jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość jest ustawiona na podstawie WARIANTu lub `COleVariant` wartości, których nie można przekonwertować na wartość walutową.

- Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji przypisywania arytmetycznego, na przykład `+=` lub **\*=** .

- Jeśli nieprawidłowa wartość została przypisana do tego obiektu.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [SetStatus](#setstatus).

Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowe, zobacz następujące funkcje Członkowskie:

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +-](#operator_plus_minus)

- [operator + = i-=](#operator_plus_minus_eq)

- [operator */](#operator_star)

- [operator * = i/=](#operator_star_div_eq)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency:: m_cur

Bazowa struktura [waluty](/windows/win32/api/wtypes/ns-wtypes-cy-r1) dla tego `COleCurrency` obiektu.

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w strukturze, `CURRENCY` do której uzyskuje dostęp wskaźnik zwracany przez tę funkcję, spowoduje zmianę wartości tego `COleCurrency` obiektu. Nie powoduje zmiany stanu tego `COleCurrency` obiektu.

Aby uzyskać więcej informacji, zobacz wpis [waluty](/windows/win32/api/wtypes/ns-wtypes-cy-r1) w Windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency:: m_status

Typ tego elementu członkowskiego danych jest typem wyliczanym `CurrencyStatus` , który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że ten `COleCurrency` obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że ten `COleCurrency` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że ten `COleCurrency` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleCurrency` obiektu jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość jest ustawiona na podstawie WARIANTu lub `COleVariant` wartości, których nie można przekonwertować na wartość walutową.

- Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji przypisywania arytmetycznego, na przykład `+=` lub **\*=** .

- Jeśli nieprawidłowa wartość została przypisana do tego obiektu.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [SetStatus](#setstatus).

Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowe, zobacz następujące funkcje Członkowskie:

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +,-](#operator_plus_minus)

- [operator + =,-=](#operator_plus_minus_eq)

- [operator */](#operator_star)

- [operator * =,/=](#operator_star_div_eq)

> [!CAUTION]
> Ten element członkowski danych ma na celu zaawansowaną sytuację programistyczną. Należy użyć wbudowanej funkcji składowej [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz, `SetStatus` Aby uzyskać dalsze ostrzeżenie dotyczące jawnego ustawiania tego elementu członkowskiego danych.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency:: operator =

Te przeciążone operatory przypisania kopiują wartość waluty źródłowej do tego `COleCurrency` obiektu.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Uwagi

Poniżej znajduje się krótki opis każdego z następujących operatorów:

- **operator = (** `cySrc` **)** `CURRENCY` wartość jest kopiowana do `COleCurrency` obiektu, a jego stan jest ustawiony na prawidłowy.

- **operator = (** `curSrc` **)** wartość i stan operandu, istniejący `COleCurrency` obiekt jest kopiowany do tego `COleCurrency` obiektu.

- **operator = (** *varSrc* **)** Jeśli konwersja `VARIANT` wartości (lub obiektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na walutę ( `VT_CY` ) powiedzie się, przekonwertowana wartość jest kopiowana do tego `COleCurrency` obiektu, a jego stan jest ustawiony na prawidłowy. Jeśli konwersja nie powiedzie się, wartość `COleCurrency` obiektu jest ustawiona na 0, a jego stan na nieprawidłowy.

Aby uzyskać więcej informacji, zobacz wartości [walutowe](/windows/win32/api/wtypes/ns-wtypes-cy-r1) i [wariantowe](/windows/win32/api/oaidl/ns-oaidl-variant) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency:: operator +,-

Te operatory umożliwiają dodawanie i odejmowanie dwóch `COleCurrency` wartości do i od siebie oraz w celu zmiany znaku `COleCurrency` wartości.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Uwagi

Jeśli jeden z operandów ma wartość null, stan `COleCurrency` wartości wyników jest równy null.

W przypadku przepełnienia operacji arytmetycznej wartość wyniki `COleCurrency` jest nieprawidłowa.

Jeśli operand jest nieprawidłowy, a drugi nie ma wartości null, stan `COleCurrency` wartości wyników jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency:: operator + =,-=

Umożliwia dodanie i odjęcie `COleCurrency` wartości do i z tego `COleCurrency` obiektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Uwagi

Jeśli jeden z operandów ma wartość null, stan tego `COleCurrency` obiektu jest ustawiony na wartość null.

W przypadku przepełnienia operacji arytmetycznej stan tego `COleCurrency` obiektu jest ustawiony na nieprawidłowy.

Jeśli jeden z operandów jest nieprawidłowy, a drugi nie ma wartości null, stan tego `COleCurrency` obiektu jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency:: operator \* i/

Umożliwia skalowanie `COleCurrency` wartości przez wartość całkowitą.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Uwagi

Jeśli `COleCurrency` operand ma wartość null, stan `COleCurrency` wartości wyników jest równy null.

Jeśli operacje arytmetyczne przepływają lub przepływają, stan `COleCurrency` wartości wyników jest nieprawidłowy.

Jeśli `COleCurrency` argument operacji jest nieprawidłowy, stan `COleCurrency` wartości wyniki jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency:: operator \* =,/=

Pozwala na skalowanie tej `COleCurrency` wartości za pomocą wartości całkowitej.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Uwagi

Jeśli `COleCurrency` operand ma wartość null, stan tego `COleCurrency` obiektu jest ustawiony na wartość null.

W przypadku przepełnienia operacji arytmetycznej stan tego `COleCurrency` obiektu jest ustawiony na nieprawidłowy.

Jeśli `COleCurrency` argument operacji jest nieprawidłowy, stan tego `COleCurrency` obiektu jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency:: operator &lt; &lt; ,&gt;&gt;

Obsługuje zrzucanie diagnostyczne i przechowywanie w archiwum.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>Uwagi

Operator wyodrębniania ( **>>** ) obsługuje ładowanie z archiwum.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency:: operator — waluta

Zwraca `CURRENCY` strukturę, której wartość jest kopiowana z tego `COleCurrency` obiektu.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Uwagi

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::P arseCurrency

Wywołaj tę funkcję elementu członkowskiego, aby przeanalizować ciąg w celu odczytania wartości walutowej.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parametry

*lpszCurrency*<br/>
Wskaźnik do ciągu zakończonego wartością null, który ma zostać przeanalizowany.

*flagiDW*<br/>
Wskazuje flagi dla ustawień regionalnych, które mogą mieć następującą flagę:

- LOCALE_NOUSEROVERRIDE Użyj domyślnych ustawień regionalnych systemu zamiast niestandardowych ustawień użytkownika.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych do użycia podczas konwersji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ciąg został pomyślnie przekonwertowany na wartość walutową, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Używa lokalnych specyfikacji języka (identyfikatorów ustawień regionalnych) dla znaczenia znaków nieliczbowych w ciągu źródłowym.

Omówienie wartości identyfikatorów ustawień regionalnych można znaleźć w temacie [Obsługa wielu języków](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Jeśli ciąg został pomyślnie przekonwertowany na wartość walutową, wartość tego `COleCurrency` obiektu jest ustawiana na tę wartość, a jego stan jest prawidłowy.

Jeśli nie można przekonwertować ciągu na wartość walutową lub w przypadku przepełnienia liczbowego, stan tego `COleCurrency` obiektu jest nieprawidłowy.

Jeśli konwersja ciągu nie powiodła się z powodu błędów alokacji pamięci, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md). W każdym innym stanie błędu ta funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operatory relacyjne COleCurrency

Porównaj dwie wartości walutowe i zwróć wartość różną od zera, jeśli warunek ma wartość PRAWDA. w przeciwnym razie 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Wartość zwracana operacji porządkowania ( **<** , **\<=**, **>** , **>=** ) jest niezdefiniowana, jeśli stan każdego operandu ma wartość null lub jest nieprawidłowy. Operatory równości ( `==` , `!=` ) uwzględniają stan operandów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency:: SetCurrency

Wywołaj tę funkcję elementu członkowskiego, aby ustawić jednostki i część ułamkową tego `COleCurrency` obiektu.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nUnits*, *nFractionalUnits* wskazują jednostki i część ułamkową (w 1/10000) wartości, która ma zostać skopiowana do tego `COleCurrency` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli wartość bezwzględna części ułamkowej jest większa niż 10 000, odpowiednie dostosowanie jest dokonywane w jednostkach, jak pokazano w trzecim z poniższych przykładów.

Należy zauważyć, że jednostki i części ułamkowe są określone przez podpisane długie wartości. W czwartym z poniższych przykładów pokazano, co się dzieje, gdy parametry mają różne znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency:: SetStatus

Wywołaj tę funkcję elementu członkowskiego, aby ustawić stan (ważność) tego `COleCurrency` obiektu.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Nowy stan dla tego `COleCurrency` obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *status* jest definiowana przez `CurrencyStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że ten `COleCurrency` obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że ten `COleCurrency` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że ten `COleCurrency` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

> [!CAUTION]
> Ta funkcja jest dla zaawansowanych sytuacji programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. Będzie najczęściej używany do ustawienia stanu na wartość null lub nieprawidłowy. Należy zauważyć, że operator przypisania ( [operator =](#operator_eq)) i [SetCurrency](#setcurrency) ustawia stan na obiekt na podstawie wartości źródłowych.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleVariant](../../mfc/reference/colevariant-class.md)
