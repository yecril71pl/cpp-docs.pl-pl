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
ms.openlocfilehash: cc69143101c5d00d4f9a689bd02abdd9596e5b53
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753923"
---
# <a name="colecurrency-class"></a>Klasa COleCurrency

Hermetyzuje `CURRENCY` typ danych automatyzacji OLE.

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
|[COleCurrency::Format](#format)|Generuje sformatowaną reprezentację `COleCurrency` ciągu obiektu.|
|[COleCurrency::GetStatus](#getstatus)|Pobiera stan (ważność) `COleCurrency` tego obiektu.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Odczytuje wartość CURRENCY z ciągu i `COleCurrency`ustawia wartość .|
|[COleCurrency::SetCurrency](#setcurrency)|Ustawia wartość tego `COleCurrency` obiektu.|
|[COleCurrency::SetStatus](#setstatus)|Ustawia stan (ważność) `COleCurrency` dla tego obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje `COleCurrency` wartość.|
|[operator +, -](#operator_plus_minus)|Dodaje, odejmuje i `COleCurrency` zmienia znak wartości.|
|[operator +=, -=](#operator_plus_minus_eq)|Dodaje i odejmuje `COleCurrency` `COleCurrency` wartość od tego obiektu.|
|[operator */](#operator_star)|Skaluje `COleCurrency` wartość o wartość całkowitą.|
|[operator *=, /=](#operator_star_div_eq)|Skaluje `COleCurrency` tę wartość o wartość całkowitą.|
|[ <<operatora](#operator_stream)|Wyprowadza `COleCurrency` wartość do `CArchive` `CDumpContext`lub .|
|[ >>operatora](#operator_stream)|Wprowadza `COleCurrency` obiekt z `CArchive`pliku .|
|[waluta operatora](#operator_currency)|Konwertuje `COleCurrency` wartość na walutę.|
|[operator ==, <, <=, itp.](#colecurrency_relational_operators)|Porównuje dwie `COleCurrency` wartości.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Zawiera podstawową walutę dla tego `COleCurrency` obiektu.|
|[COleCurrency::m_status](#m_status)|Zawiera stan tego `COleCurrency` obiektu.|

## <a name="remarks"></a>Uwagi

`COleCurrency`nie ma klasy podstawowej.

WALUTA jest implementowana jako 8-bajtowa, wartość całkowita dwóch uzupełnianych całkowitej skalowanej przez 10 000. Daje to stały numer punktowy z 15 cyframi po lewej stronie przecinka dziesiętnego i 4 cyframi po prawej stronie. Typ danych CURRENCY jest niezwykle przydatny w obliczeniach dotyczących pieniądza lub do obliczeń stałych, w których dokładność jest ważna. Jest to jeden z możliwych `VARIANT` typów dla typu danych automatyzacji OLE.

`COleCurrency`implementuje również niektóre podstawowe operacje arytmetyczne dla tego typu stałego punktu. Obsługiwane operacje zostały wybrane do kontrolowania błędów zaokrąglania, które występują podczas obliczeń stałych punktów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleCurrency`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

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

*cysrc (cysrc)*<br/>
Wartość CURRENCY, która ma zostać `COleCurrency` skopiowana do nowego obiektu.

*curSrc ( curSrc )*<br/>
Istniejący `COleCurrency` obiekt do skopiowania `COleCurrency` do nowego obiektu.

*varSrc ( varSrc )*<br/>
Istniejąca `VARIANT` struktura danych `COleVariant` (ewentualnie obiekt) ma zostać przekonwertowana na wartość waluty `COleCurrency` (VT_CY) i skopiowana do nowego obiektu.

*nJednostki*, *nFractionalUnits* Wskazać jednostki i część ułamkową (w 1/10 000) `COleCurrency` wartości, która ma zostać skopiowana do nowego obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory utworzyć nowe `COleCurrency` obiekty zainicjowane do określonej wartości. Krótki opis każdego z tych konstruktorów następuje. O ile nie zaznaczono `COleCurrency` inaczej, stan nowego elementu jest ustawiony na prawidłowy.

- COleCurrency() Konstruuje `COleCurrency` obiekt zainicjowany do 0 (zero).

- COleCurrency(`cySrc`) Konstruuje `COleCurrency` obiekt z wartości [CURRENCY.](/windows/win32/api/wtypes/ns-wtypes-cy~r1)

- COleCurrency(`curSrc`) Konstruuje `COleCurrency` obiekt `COleCurrency` z istniejącego obiektu. Nowy obiekt ma taki sam stan jak obiekt źródłowy.

- COleCurrency(`varSrc`) Konstruuje `COleCurrency` obiekt. Próbuje przekonwertować `COleVariant` strukturę [WARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) lub obiekt na wartość waluty (VT_CY). Jeśli ta konwersja zakończy się pomyślnie, przekonwertowana wartość jest kopiowana do nowego `COleCurrency` obiektu. Jeśli tak nie jest, `COleCurrency` wartość obiektu jest ustawiona na zero (0), a jego stan na nieprawidłowy.

- COleCurrency(`nUnits` `nFractionalUnits`, ) `COleCurrency` Konstruuje obiekt z określonych komponentów liczbowych. Jeżeli wartość bezwzględna części ułamkowej jest większa niż 10 000, dokonuje się odpowiedniej korekty w jednostkach. Należy zauważyć, że jednostki i część ułamkowa są określone przez podpisane wartości długie.

Aby uzyskać więcej informacji, zobacz [wpisy WALUTA](/windows/win32/api/wtypes/ns-wtypes-cy~r1) i [WARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) w sdk systemu Windows.

### <a name="example"></a>Przykład

Poniższe przykłady przedstawiają efekty konstruktorów zero-parameter i two-parameter:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency::Format

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć sformatowaną reprezentację wartości waluty.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Wskazuje flagi dla ustawień regionalnych. Tylko następująca flaga jest odpowiednia dla waluty:

- LOCALE_NOUSEROVERRIDE Use the system default locale settings, rather than custom user settings.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych, który ma być używany do konwersji.

### <a name="return-value"></a>Wartość zwracana

A `CString` zawierający sformatowaną wartość waluty.

### <a name="remarks"></a>Uwagi

Formatuje wartość przy użyciu lokalnych specyfikacji języka (identyfikatory ustawień regionalnych). Symbol waluty nie jest uwzględniany w zwróconej wartości. Jeśli stan tego `COleCurrency` obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określony przez IDS_INVALID_CURRENCY zasobu ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać `COleCurrency` stan (ważność) danego obiektu.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan tej `COleCurrency` wartości.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest `CurrencyStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że `COleCurrency` ten obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że `COleCurrency` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że `COleCurrency` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

Stan obiektu `COleCurrency` jest nieprawidłowy w następujących przypadkach:

- Jeśli jego wartość jest ustawiona na podstawie wariantu lub `COleVariant` wartości, których nie można przekonwertować na wartość waluty.

- Jeśli ten obiekt doświadczył przepełnienia lub niedopełnienia podczas operacji `+=` przypisania arytmetycznego, na przykład lub ** \* **.

- Jeśli do tego obiektu została przypisana nieprawidłowa wartość.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [setstatus](#setstatus).

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz następujące funkcje członkowskie:

- [Colecurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator + -](#operator_plus_minus)

- [operator += i -=](#operator_plus_minus_eq)

- [operator * /](#operator_star)

- [operator *= i /=](#operator_star_div_eq)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency::m_cur

Podstawowa [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) struktura WALUTY `COleCurrency` dla tego obiektu.

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w `CURRENCY` strukturze dostępnej za pomocą wskaźnika zwróconego `COleCurrency` przez tę funkcję spowoduje zmianę wartości tego obiektu. Nie zmienia stanu tego `COleCurrency` obiektu.

Aby uzyskać więcej informacji, zobacz wpis [WALUTY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) w windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency::m_status

Typ tego elementu członkowskiego danych jest typem `CurrencyStatus`wyliczonym, który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że `COleCurrency` ten obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że `COleCurrency` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że `COleCurrency` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

Stan obiektu `COleCurrency` jest nieprawidłowy w następujących przypadkach:

- Jeśli jego wartość jest ustawiona na podstawie wariantu lub `COleVariant` wartości, których nie można przekonwertować na wartość waluty.

- Jeśli ten obiekt doświadczył przepełnienia lub niedopełnienia podczas operacji `+=` przypisania arytmetycznego, na przykład lub ** \* **.

- Jeśli do tego obiektu została przypisana nieprawidłowa wartość.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [setstatus](#setstatus).

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz następujące funkcje członkowskie:

- [Colecurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +, -](#operator_plus_minus)

- [operator +=, -=](#operator_plus_minus_eq)

- [operator */](#operator_star)

- [operator *=, /=](#operator_star_div_eq)

> [!CAUTION]
> Ten element członkowski danych jest przeznaczony do zaawansowanych sytuacji programowania. Należy użyć wbudowanych funkcji członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dalsze ostrzeżenia dotyczące jawnego ustawiania tego elementu członkowskiego danych.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::operator =

Te przeciążone operatory przypisania kopiują wartość waluty źródłowej do tego `COleCurrency` obiektu.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Uwagi

Krótki opis każdego operatora jest następujący:

- **operator =(** `cySrc` **)** Wartość `CURRENCY` jest kopiowana `COleCurrency` do obiektu, a jego stan jest ustawiony na prawidłowy.

- **operator =(** `curSrc` **)** Wartość i stan operandu, `COleCurrency` istniejący obiekt są `COleCurrency` kopiowane do tego obiektu.

- **operator =(** *varSrc* **)** Jeśli konwersja `VARIANT` wartości (lub [COleVariant](../../mfc/reference/colevariant-class.md) object) `VT_CY`na walutę ( ) zakończy się `COleCurrency` pomyślnie, przekonwertowana wartość jest kopiowana do tego obiektu, a jego stan jest ustawiony na prawidłowy. Jeśli konwersja nie powiedzie się, wartość obiektu jest ustawiona `COleCurrency` na 0, a jego stan na nieprawidłowy.

Aby uzyskać więcej informacji, zobacz [wpisy WALUTA](/windows/win32/api/wtypes/ns-wtypes-cy~r1) i [WARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) w sdk systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::operator +, -

Operatory te umożliwiają dodawanie i `COleCurrency` odejmowanie dwóch wartości do i `COleCurrency` od siebie oraz zmianę znaku wartości.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Uwagi

Jeśli którykolwiek z argumentów ma wartość null, `COleCurrency` stan wartości wynikowej jest zerowy.

Jeśli operacja arytmetyczna zostanie przepełniona, wynikowa `COleCurrency` wartość jest nieprawidłowa.

Jeśli operand jest nieprawidłowy, a drugi nie ma `COleCurrency` wartości null, stan wynikowej wartości jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::operator +=, -=

Umożliwia dodawanie i odejmowanie `COleCurrency` wartości do `COleCurrency` i z tego obiektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Uwagi

Jeśli którykolwiek z argumentów ma wartość null, stan tego `COleCurrency` obiektu jest ustawiony na wartość null.

Jeśli operacja arytmetyczna zostanie przepełniona, `COleCurrency` stan tego obiektu jest ustawiony na nieprawidłowy.

Jeśli którykolwiek z argumentów jest nieprawidłowy, a drugi nie `COleCurrency` ma wartości null, stan tego obiektu jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::operator \* i /

Umożliwia skalowanie `COleCurrency` wartości za pomocą wartości integralnej.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Uwagi

Jeśli `COleCurrency` operand ma wartość null, stan `COleCurrency` wartości wynikowej jest zerowy.

Jeśli operacja arytmetyczna przepełnia się lub niedopełnia, `COleCurrency` stan wynikowej wartości jest nieprawidłowy.

Jeśli `COleCurrency` operand jest nieprawidłowy, stan `COleCurrency` wynikowej wartości jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::operator \*=, /=

Umożliwia skalowanie `COleCurrency` tej wartości przez wartość całkowitą.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Uwagi

Jeśli `COleCurrency` operand ma wartość null, `COleCurrency` stan tego obiektu jest ustawiony na wartość null.

Jeśli operacja arytmetyczna zostanie przepełniona, `COleCurrency` stan tego obiektu jest ustawiony na nieprawidłowy.

Jeśli `COleCurrency` operand jest nieprawidłowy, `COleCurrency` stan tego obiektu jest ustawiony na nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::operator &lt; &lt;,&gt;&gt;

Obsługuje diagnostykę dumpingu i przechowywania w archiwum.

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

Operator ekstrakcji ( **>>**) obsługuje ładowanie z archiwum.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::operator WALUTA

Zwraca `CURRENCY` strukturę, której wartość `COleCurrency` jest kopiowana z tego obiektu.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Uwagi

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::ParseCurrency

Wywołanie tej funkcji elementu członkowskiego, aby przeanalizować ciąg, aby odczytać wartość waluty.

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
Wskaźnik do ciągu zakończonego wartością null, który ma być analizowany.

*Dwflags*<br/>
Wskazuje flagi dla ustawień regionalnych, ewentualnie następującą flagę:

- LOCALE_NOUSEROVERRIDE Use the system default locale settings, rather than custom user settings.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych, który ma być używany do konwersji.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli ciąg został pomyślnie przekonwertowany na wartość waluty, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Używa specyfikacji języka lokalnego (identyfikatory ustawień regionalnych) dla znaczenia znaków nielicznych w ciągu źródłowym.

Aby zapoznać się z omówieniem wartości identyfikatorów ustawień [regionalnych,](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)zobacz Obsługa wielu języków .

Jeśli ciąg został pomyślnie przekonwertowany na `COleCurrency` wartość waluty, wartość tego obiektu jest ustawiona na tę wartość, a jego stan na prawidłowy.

Jeśli nie można przekonwertować ciągu na wartość waluty lub wystąpiło przepełnienie numeryczne, stan tego `COleCurrency` obiektu jest nieprawidłowy.

Jeśli konwersja ciągów nie powiodła się z powodu błędów alokacji pamięci, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md). W każdym innym stanie błędu ta funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operatory relacyjne COleCurrency

Porównaj dwie wartości waluty i zwrot bezzerowy, jeśli warunek jest spełniony; w przeciwnym razie 0.

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
> Zwracana wartość operacji zamawiania **<** ** \< **( **>** **>=**, , , ) jest niezdefiniowana, jeśli stan albo operand jest null lub nieprawidłowy. Operatory równości `==` `!=`( , ) biorą pod uwagę stan operands.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Wywołanie tej funkcji elementu członkowskiego, aby `COleCurrency` ustawić jednostki i ułamkową część tego obiektu.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nJednostki*, *nFractionalUnits* Wskazać jednostki i część ułamkową (w 1/10 000) `COleCurrency` wartości, która ma zostać skopiowana do tego obiektu.

### <a name="remarks"></a>Uwagi

Jeżeli wartość bezwzględna części ułamkowej jest większa niż 10 000, dokonuje się odpowiedniej korekty w jednostkach, jak pokazano w trzecim z poniższych przykładów.

Należy zauważyć, że jednostki i część ułamkowa są określone przez podpisane wartości długie. Czwarty z poniższych przykładów pokazuje, co się dzieje, gdy parametry mają różne znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus

Wywołanie tej funkcji elementu członkowskiego, aby `COleCurrency` ustawić stan (ważność) tego obiektu.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*Stan*<br/>
Nowy stan dla `COleCurrency` tego obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *stanu* jest `CurrencyStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleCurrency` klasie.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleCurrency::valid`Wskazuje, że `COleCurrency` ten obiekt jest prawidłowy.

- `COleCurrency::invalid`Wskazuje, że `COleCurrency` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleCurrency::null`Wskazuje, że `COleCurrency` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

> [!CAUTION]
> Ta funkcja jest dla zaawansowanych sytuacji programowania. Ta funkcja nie zmienia danych w tym obiekcie. Najczęściej będzie używany do ustawiania stanu na null lub nieprawidłowy. Należy zauważyć, że operator przypisania ( [operator =](#operator_eq)) i [SetCurrency](#setcurrency) ustawiają stan obiektu na podstawie wartości źródłowych.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleVariant](../../mfc/reference/colevariant-class.md)
