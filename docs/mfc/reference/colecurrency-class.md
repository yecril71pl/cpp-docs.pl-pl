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
ms.openlocfilehash: 1e32d75599f51ba277180341df60762a02a82fe5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150932"
---
# <a name="colecurrency-class"></a>Klasa COleCurrency

Hermetyzuje typ danych `CURRENCY` automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleCurrency
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Konstruuje obiekt `COleCurrency`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleCurrency:: format](#format)|Generuje sformatowaną reprezentację ciągu obiektu `COleCurrency`.|
|[COleCurrency:: GetStatus](#getstatus)|Pobiera stan (ważność) tego obiektu `COleCurrency`.|
|[COleCurrency::P arseCurrency](#parsecurrency)|Odczytuje wartość waluty z ciągu i ustawia wartość `COleCurrency`.|
|[COleCurrency:: SetCurrency](#setcurrency)|Ustawia wartość tego obiektu `COleCurrency`.|
|[COleCurrency:: SetStatus](#setstatus)|Ustawia stan (ważność) dla tego obiektu `COleCurrency`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje wartość `COleCurrency`.|
|[operator +,-](#operator_plus_minus)|Dodaje, odejmuje i zmienia znak `COleCurrency` wartości.|
|[operator + =,-=](#operator_plus_minus_eq)|Dodaje i odejmuje wartość `COleCurrency` z tego obiektu `COleCurrency`.|
|[operator */](#operator_star)|Skaluje wartość `COleCurrency` za pomocą wartości całkowitej.|
|[operator * =,/=](#operator_star_div_eq)|Skaluje tę wartość `COleCurrency` za pomocą wartości całkowitej.|
|[< operatora <](#operator_stream)|Wyprowadza `COleCurrency` wartość do `CArchive` lub `CDumpContext`.|
|[> operatora >](#operator_stream)|Wprowadza `COleCurrency` obiekt z `CArchive`.|
|[Waluta operatora](#operator_currency)|Konwertuje wartość `COleCurrency` na WALUTę.|
|[operator = =, <, < = itd.](#colecurrency_relational_operators)|Porównuje dwie wartości `COleCurrency`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|Zawiera podstawową WALUTę dla tego obiektu `COleCurrency`.|
|[COleCurrency:: m_status](#m_status)|Zawiera stan tego obiektu `COleCurrency`.|

## <a name="remarks"></a>Uwagi

`COleCurrency` nie ma klasy bazowej.

WALUTA jest zaimplementowana jako 8-bajtowa, dwie wartości całkowite do uzupełnienia, skalowane przez 10 000. Daje to stałą liczbę z 15 cyfr po lewej stronie przecinka dziesiętnego i 4 cyfry po prawej stronie. Typ danych WALUTowych jest niezwykle przydatny do obliczeń związanych z pieniędzmi lub w przypadku obliczeń o stałej liczbie, w których dokładność jest ważna. Jest to jeden z możliwych typów dla `VARIANT` typ danych automatyzacji OLE.

`COleCurrency` implementuje także podstawowe operacje arytmetyczne dla tego typu stałego. Zostały wybrane obsługiwane operacje w celu kontrolowania błędów zaokrąglania występujących podczas obliczeń z ustalonym punktem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleCurrency`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

Konstruuje obiekt `COleCurrency`.

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
Wartość waluty, która ma zostać skopiowana do nowego obiektu `COleCurrency`.

*curSrc*<br/>
Istniejący obiekt `COleCurrency`, który ma zostać skopiowany do nowego obiektu `COleCurrency`.

*varSrc*<br/>
Istniejąca struktura danych `VARIANT` (prawdopodobnie obiekt `COleVariant`) do przekonwertowania na wartość walutową (VT_CY) i skopiowana do nowego obiektu `COleCurrency`.

*nUnits*, *nFractionalUnits* wskazują jednostki i część ułamkową (w 1/10000) wartości, która ma zostać skopiowana do nowego obiektu `COleCurrency`.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe obiekty `COleCurrency` zainicjowane do określonej wartości. Poniżej znajduje się krótki opis każdego z tych konstruktorów. O ile nie zaznaczono inaczej, stan nowego elementu `COleCurrency` jest ustawiony na wartość prawidłowy.

- COleCurrency () konstruuje obiekt `COleCurrency` zainicjowany do 0 (zero).

- COleCurrency (`cySrc`) konstruuje obiekt `COleCurrency` z wartości [walutowej](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .

- COleCurrency (`curSrc`) konstruuje obiekt `COleCurrency` z istniejącego obiektu `COleCurrency`. Nowy obiekt ma ten sam stan co obiekt źródłowy.

- COleCurrency (`varSrc`) konstruuje obiekt `COleCurrency`. Próbuje skonwertować strukturę [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) lub `COleVariant` obiektu na wartość walutową (VT_CY). Jeśli ta konwersja zakończyła się pomyślnie, przekonwertowana wartość jest kopiowana do nowego obiektu `COleCurrency`. Jeśli tak nie jest, wartość obiektu `COleCurrency` jest równa zero (0), a jego stan jest nieprawidłowy.

- COleCurrency (`nUnits`, `nFractionalUnits`) konstruuje obiekt `COleCurrency` z określonych składników liczbowych. Jeśli wartość bezwzględna części ułamkowej jest większa niż 10 000, odpowiednie dostosowanie jest dokonywane w jednostkach. Należy zauważyć, że jednostki i części ułamkowe są określone przez podpisane długie wartości.

Aby uzyskać więcej informacji, zobacz wartości [walutowe](/windows/win32/api/wtypes/ns-wtypes-cy~r1) i [wariantowe](/windows/win32/api/oaidl/ns-oaidl-variant) w Windows SDK.

### <a name="example"></a>Przykład

Poniższe przykłady przedstawiają efekty konstruktorów z parametrem zero i dwoma parametrami:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency:: format

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

`CString`, który zawiera sformatowaną wartość waluty.

### <a name="remarks"></a>Uwagi

Wartość ta jest formatowana przy użyciu lokalnych specyfikacji języka (identyfikatorów ustawień regionalnych). Symbol waluty nie jest uwzględniony w zwracanej wartości. Jeśli stan tego obiektu `COleCurrency` ma wartość null, zwracana wartość jest ciągiem pustym. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określany przez zasób ciągu IDS_INVALID_CURRENCY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency:: GetStatus

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać stan (ważność) danego obiektu `COleCurrency`.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan tej wartości `COleCurrency`.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowana przez `CurrencyStatus` typ wyliczeniowy, który jest zdefiniowany w klasie `COleCurrency`.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

  - `COleCurrency::valid` wskazuje, że ten obiekt `COleCurrency` jest prawidłowy.

  - `COleCurrency::invalid` wskazuje, że ten obiekt `COleCurrency` jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

  - `COleCurrency::null` wskazuje, że ten obiekt `COleCurrency` ma wartość null, oznacza to, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez żadnej wartości", w przeciwieństwie do C++ wartości null).

Stan obiektu `COleCurrency` jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość jest ustawiona na podstawie wartości typu VARIANT lub `COleVariant`, której nie można przekonwertować na wartość walutową.

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

##  <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency:: m_cur

Bazowa struktura [waluty](/windows/win32/api/wtypes/ns-wtypes-cy~r1) dla tego obiektu `COleCurrency`.

### <a name="remarks"></a>Uwagi

> [!CAUTION]
>  Zmiana wartości w strukturze `CURRENCY`, do której uzyskuje się wskaźnik zwrócony przez tę funkcję, spowoduje zmianę wartości tego obiektu `COleCurrency`. Nie powoduje zmiany stanu tego obiektu `COleCurrency`.

Aby uzyskać więcej informacji, zobacz wpis [waluty](/windows/win32/api/wtypes/ns-wtypes-cy~r1) w Windows SDK.

##  <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency:: m_status

Typ tego elementu członkowskiego danych jest typem wyliczanym `CurrencyStatus`, który jest zdefiniowany w klasie `COleCurrency`.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid` wskazuje, że ten obiekt `COleCurrency` jest prawidłowy.

- `COleCurrency::invalid` wskazuje, że ten obiekt `COleCurrency` jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null` wskazuje, że ten obiekt `COleCurrency` ma wartość null, oznacza to, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez żadnej wartości", w przeciwieństwie do C++ wartości null).

Stan obiektu `COleCurrency` jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość jest ustawiona na podstawie wartości typu VARIANT lub `COleVariant`, której nie można przekonwertować na wartość walutową.

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
>  Ten element członkowski danych ma na celu zaawansowaną sytuację programistyczną. Należy użyć wbudowanej funkcji składowej [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus`, aby uzyskać dalsze ostrzeżenie dotyczące jawnego ustawiania tego elementu członkowskiego danych.

##  <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency:: operator =

Te przeciążone operatory przypisania kopiują wartość waluty źródłowej do tego obiektu `COleCurrency`.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Uwagi

Poniżej znajduje się krótki opis każdego z następujących operatorów:

- **operator = (** `cySrc` **)** Wartość `CURRENCY` jest kopiowana do obiektu `COleCurrency`, a jego stan jest ustawiony na prawidłowy.

- **operator = (** `curSrc` **)** Wartość i stan operandu, istniejący obiekt `COleCurrency` są kopiowane do tego obiektu `COleCurrency`.

- **operator = (** *varSrc* **)** Jeśli konwersja wartości `VARIANT` (lub obiektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na walutę (`VT_CY`) zakończyła się pomyślnie, przekonwertowana wartość jest kopiowana do tego obiektu `COleCurrency` i jego stan jest ustawiony na wartość prawidłowy. Jeśli konwersja nie powiedzie się, wartość obiektu `COleCurrency` jest ustawiona na 0, a jego stan na nieprawidłowy.

Aby uzyskać więcej informacji, zobacz wartości [walutowe](/windows/win32/api/wtypes/ns-wtypes-cy~r1) i [wariantowe](/windows/win32/api/oaidl/ns-oaidl-variant) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency:: operator +,-

Te operatory umożliwiają dodawanie i odejmowanie dwóch wartości `COleCurrency` do i od siebie oraz do zmiany znaku `COleCurrency` wartości.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Uwagi

Jeśli jeden z operandów ma wartość null, stan wyników `COleCurrency` wartość null.

W przypadku przepełnienia operacji arytmetycznej wartość `COleCurrency`, która jest nieprawidłowa.

Jeśli operand jest nieprawidłowy, a drugi nie ma wartości null, stan wynikającej `COleCurrency` wartość jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency:: operator + =,-=

Zezwól na dodawanie i odejmowanie wartości `COleCurrency` do i z tego `COleCurrency`go obiektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Uwagi

Jeśli jeden z operandów ma wartość null, stan tego obiektu `COleCurrency` jest ustawiony na wartość null.

W przypadku przepełnienia operacji arytmetycznej stan tego obiektu `COleCurrency` jest ustawiony na nieprawidłowy.

Jeśli jeden z operandów jest nieprawidłowy, a drugi nie ma wartości null, stan tego obiektu `COleCurrency` jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency:: operator \* i/

Umożliwia skalowanie wartości `COleCurrency` przez wartość całkowitą.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Uwagi

Jeśli operand `COleCurrency` ma wartość null, stan obliczonej `COleCurrency` wartość ma wartość null.

W przypadku przepełnienia lub podpełnienia operacji arytmetycznej stan wartości `COleCurrency` wartość jest nieprawidłowy.

Jeśli operand `COleCurrency` jest nieprawidłowy, stan wynikającej `COleCurrency` wartość jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency:: operator \*=,/=

Umożliwia skalowanie tej wartości `COleCurrency` przez wartość całkowitą.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Uwagi

Jeśli operand `COleCurrency` ma wartość null, stan tego obiektu `COleCurrency` jest ustawiony na wartość null.

W przypadku przepełnienia operacji arytmetycznej stan tego obiektu `COleCurrency` jest ustawiony na nieprawidłowy.

Jeśli operand `COleCurrency` jest nieprawidłowy, stan tego obiektu `COleCurrency` jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency:: operator &lt;&lt;, &gt;&gt;

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

##  <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency:: operator — waluta

Zwraca strukturę `CURRENCY`, której wartość jest kopiowana z tego obiektu `COleCurrency`.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Uwagi

##  <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::P arseCurrency

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

Jeśli ciąg został pomyślnie przekonwertowany na wartość walutową, wartość tego obiektu `COleCurrency` jest ustawiona na tę wartość, a jego stan jest prawidłowy.

Jeśli nie można przekonwertować ciągu na wartość waluty lub w przypadku przepełnienia liczbowego, stan tego obiektu `COleCurrency` jest nieprawidłowy.

Jeśli konwersja ciągu nie powiodła się z powodu błędów alokacji pamięci, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md). W każdym innym stanie błędu ta funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operatory relacyjne COleCurrency

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
>  Wartość zwracana operacji porządkowania ( **<** , **\<=** , **>** , **>=** ) jest niezdefiniowana, jeśli stan dowolnego operandu ma wartość null lub jest nieprawidłowy. Operatory równości (`==`, `!=`) uwzględniają stan operandów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency:: SetCurrency

Wywołaj tę funkcję elementu członkowskiego, aby ustawić jednostki i część ułamkową tego obiektu `COleCurrency`.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nUnits*, *nFractionalUnits* wskazują jednostki i część ułamkową (w 1/10000) wartości, która ma zostać skopiowana do tego obiektu `COleCurrency`.

### <a name="remarks"></a>Uwagi

Jeśli wartość bezwzględna części ułamkowej jest większa niż 10 000, odpowiednie dostosowanie jest dokonywane w jednostkach, jak pokazano w trzecim z poniższych przykładów.

Należy zauważyć, że jednostki i części ułamkowe są określone przez podpisane długie wartości. W czwartym z poniższych przykładów pokazano, co się dzieje, gdy parametry mają różne znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency:: SetStatus

Wywołaj tę funkcję elementu członkowskiego, aby ustawić stan (ważność) tego obiektu `COleCurrency`.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Nowy stan dla tego obiektu `COleCurrency`.

### <a name="remarks"></a>Uwagi

Wartość parametru *status* jest definiowana przez `CurrencyStatus` typ wyliczeniowy, który jest zdefiniowany w klasie `COleCurrency`.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid` wskazuje, że ten obiekt `COleCurrency` jest prawidłowy.

- `COleCurrency::invalid` wskazuje, że ten obiekt `COleCurrency` jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null` wskazuje, że ten obiekt `COleCurrency` ma wartość null, oznacza to, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez żadnej wartości", w przeciwieństwie do C++ wartości null).

> [!CAUTION]
>  Ta funkcja jest dla zaawansowanych sytuacji programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. Będzie najczęściej używany do ustawienia stanu na wartość null lub nieprawidłowy. Należy zauważyć, że operator przypisania ( [operator =](#operator_eq)) i [SetCurrency](#setcurrency) ustawia stan na obiekt na podstawie wartości źródłowych.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleVariant](../../mfc/reference/colevariant-class.md)
