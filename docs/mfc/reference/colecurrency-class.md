---
title: Klasa COleCurrency | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a26bae54e267dfa46b0ec8e6770b3643cc0b7ebb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681775"
---
# <a name="colecurrency-class"></a>Klasa COleCurrency
Hermetyzuje `CURRENCY` typ danych w automatyzacji OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleCurrency  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCurrency::COleCurrency](#colecurrency)|Konstruuje `COleCurrency` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCurrency::Format](#format)|Generuje reprezentację ciągu sformatowaną `COleCurrency` obiektu.|  
|[COleCurrency::GetStatus](#getstatus)|Pobiera stan (ważność) to `COleCurrency` obiektu.|  
|[COleCurrency::ParseCurrency](#parsecurrency)|Odczytuje wartość waluty z ciągu i ustawia wartość `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Ustawia wartość tego `COleCurrency` obiektu.|  
|[COleCurrency::SetStatus](#setstatus)|Ustawia stan (ważność), w tym `COleCurrency` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Kopiuje `COleCurrency` wartość.|  
|[operator +, -](#operator_plus_minus)|Dodaje, odejmuje i zmienia znak `COleCurrency` wartości.|  
|[operator +=-=](#operator_plus_minus_eq)|Dodaje i odejmuje `COleCurrency` wartości z tego `COleCurrency` obiektu.|  
|[operator * /](#operator_star)|Skaluje `COleCurrency` wartości przez wartość całkowitą.|  
|[operator * =, / =](#operator_star_div_eq)|Umożliwia to skalowanie `COleCurrency` wartości przez wartość całkowitą.|  
|[Operator <<](#operator_stream)|Dane wyjściowe `COleCurrency` wartość `CArchive` lub `CDumpContext`.|  
|[operator >>](#operator_stream)|Dane wejściowe `COleCurrency` obiektu z `CArchive`.|  
|[Operator waluty](#operator_currency)|Konwertuje `COleCurrency` wartość w walucie.|  
|[operator ==, <, < = itp.](#colecurrency_relational_operators)|Porównuje dwa `COleCurrency` wartości.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Zawiera podstawowe waluty dla tego `COleCurrency` obiektu.|  
|[COleCurrency::m_status](#m_status)|Zawiera informacje o stanie tego `COleCurrency` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleCurrency` nie ma klasy bazowej.  
  
 WALUTA jest implementowany jako 8-bajtowych, wartości całkowitej uzupełnienia do dwóch skalowania przez 10 000. Dzięki temu stałoprzecinkowa liczba z 15 cyfr z lewej strony punktu dziesiętnego i 4 cyfr po prawej stronie. Typ danych walutowych jest niezwykle przydatna funkcja obliczeń walutowych lub wszystkie obliczenia stałoprzecinkowe których dokładności jest ważna. Jest jednym z możliwych typów dla `VARIANT` typ danych w automatyzacji OLE.  
  
 `COleCurrency` implementuje również pewne podstawowe operacje arytmetyczne dla tego typu stałoprzecinkowa. Obsługiwane operacje zostały wybrane do kontrolowania błędy zaokrągleń, które występują podczas obliczeń stałoprzecinkowego.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `COleCurrency`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="colecurrency"></a>  COleCurrency::COleCurrency  
 Konstruuje `COleCurrency` obiektu.  
  
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
 *cySrc*  
 Wartość waluty do skopiowania w nowe `COleCurrency` obiektu.  
  
 *curSrc*  
 Istniejące `COleCurrency` obiektu do skopiowania w nowe `COleCurrency` obiektu.  
  
 *varSrc*  
 Istniejące `VARIANT` struktury danych (prawdopodobnie `COleVariant` obiektu) można przekonwertować na wartość waluty (VT_CY) i skopiowane do nowego `COleCurrency` obiektu.  
  
 *nUnits*, *nFractionalUnits*  
 Wskazuje jednostek i część ułamkową (w 1/10 000's) wartość do skopiowania w nowe `COleCurrency` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktory tworzą nowe `COleCurrency` obiektów inicjowane z podaną wartością. Krótki opis każdego z tych konstruktorów poniżej. Jeśli nie określono inaczej, stan nowego `COleCurrency` elementu jest ustawiony na prawidłowy.  
  
- Konstrukcje COleCurrency() `COleCurrency` obiektu inicjowane na wartość 0 (zero).  
  
- COleCurrency (`cySrc`) tworzy `COleCurrency` obiektu z [waluty](/windows/desktop/api/wtypes/ns-wtypes-tagcy) wartość.  
  
- COleCurrency (`curSrc`) tworzy `COleCurrency` obiektu z istniejącego `COleCurrency` obiektu. Nowy obiekt ma ten sam stan, co obiekt źródłowy.  
  
- COleCurrency (`varSrc`) tworzy `COleCurrency` obiektu. Stara się przekonwertować [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) struktury lub `COleVariant` obiektu jako wartość waluty (VT_CY). Jeśli ta konwersja zakończy się pomyślnie, przekonwertowana wartości jest kopiowana do nowej `COleCurrency` obiektu. Jeśli nie, to wartość `COleCurrency` obiekt jest ustawiony na wartość zero (0) i jej stanie się nieprawidłowy.  
  
- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency "obiektu z określonym składników liczbowych. Jeśli wartość bezwzględna część ułamkową jest większa niż 10 000, odpowiednie dostosowania do jednostek. Należy zauważyć, że jednostki i część ułamkową są określone przez podpisany długich wartości.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](/windows/desktop/api/wtypes/ns-wtypes-tagcy) i [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) wpisów w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach pokazano skutki konstruktory parametr zero i dwóch parametrów:  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>  COleCurrency::Format  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć sformatowany reprezentacja wartości waluty.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Parametry  
 *Flagidw*  
 Określa flagi dla ustawień regionalnych. Dotyczy tylko następujące flagi walucie:  
  
- LOCALE_NOUSEROVERRIDE używane domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.  
  
 *lcid*  
 Określa identyfikator ustawień regionalnych na potrzeby konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element `CString` zawierający wartość waluty sformatowany.  
  
### <a name="remarks"></a>Uwagi  
 Operacja formatowania wartości przy użyciu specyfikacji język lokalny (identyfikatory ustawień regionalnych). Symbol waluty, nie znajduje się w wartości zwracanej. Jeśli stan to `COleCurrency` obiekt ma wartość null, wartość zwracana jest ciągiem pustym. Jeśli stan jest nieprawidłowa, zwracanego ciągu jest określany przez zasób ciągu IDS_INVALID_CURRENCY.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>  COleCurrency::GetStatus  
 Wywołaj tę funkcję elementu członkowskiego, aby wyświetlić stan (ważność) danego `COleCurrency` obiektu.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca stan to `COleCurrency` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest definiowany przez `CurrencyStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleCurrency` klasy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:  
  
  - `COleCurrency::valid` Wskazuje, że `COleCurrency` obiekt jest prawidłowy.  
  
  - `COleCurrency::invalid` Wskazuje, że `COleCurrency` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.  
  
  - `COleCurrency::null` Wskazuje, że `COleCurrency` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).  
  
 Stan `COleCurrency` obiekt jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli wartość zostanie ustawiona z WARIANTU lub `COleVariant` wartość, która nie można przekonwertować na wartość waluty.  
  
-   Ten obiekt zawiera spowodować przepełnienie lub niedopełnienie podczas operacji arytmetycznych przypisania, na przykład `+=` lub **\* =**.  
  
-   Jeśli wartość jest nieprawidłowa został przypisany do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłowy przy użyciu [SetStatus](#setstatus).  
  
 Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan nieprawidłowy, zobacz następujące funkcje elementów członkowskich:  
  
 - [COleCurrency](#colecurrency)  
  
 - [operator =](#operator_eq)  
  
 - [operator + —](#operator_plus_minus)  
  
 - [operator += i-=](#operator_plus_minus_eq)  
  
 - [operator * /](#operator_star)  
  
 - [operator * = i / =](#operator_star_div_eq)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="m_cur"></a>  COleCurrency::m_cur  
 Podstawowe [waluty](/windows/desktop/api/wtypes/ns-wtypes-tagcy) struktury, w tym `COleCurrency` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Zmiana wartości w `CURRENCY` struktury używane przez wskaźnik zwracany przez tę funkcję zmieni wartość tego `COleCurrency` obiektu. Nie zmienia się jego stan to `COleCurrency` obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](/windows/desktop/api/wtypes/ns-wtypes-tagcy) wejścia w zestawie Windows SDK.  
  
##  <a name="m_status"></a>  COleCurrency::m_status  
 Typ ten element członkowski danych jest Typ wyliczany `CurrencyStatus`, który jest zdefiniowany w obrębie `COleCurrency` klasy.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Uwagi  
Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:  
  
 - `COleCurrency::valid` Wskazuje, że `COleCurrency` obiekt jest prawidłowy.  
      
 - `COleCurrency::invalid` Wskazuje, że `COleCurrency` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.  
      
 - `COleCurrency::null` Wskazuje, że `COleCurrency` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).  
  
Stan `COleCurrency` obiekt jest nieprawidłowy w następujących przypadkach:  
  
 - Jeśli wartość zostanie ustawiona z WARIANTU lub `COleVariant` wartość, która nie można przekonwertować na wartość waluty.  
      
 - Ten obiekt zawiera spowodować przepełnienie lub niedopełnienie podczas operacji arytmetycznych przypisania, na przykład `+=` lub **\* =**.  
      
 - Jeśli wartość jest nieprawidłowa został przypisany do tego obiektu.  
      
 - Jeśli stan tego obiektu jawnie ustawiono nieprawidłowy przy użyciu [SetStatus](#setstatus).  
  
Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan nieprawidłowy, zobacz następujące funkcje elementów członkowskich:  
  
 - [COleCurrency](#colecurrency)  
      
 - [operator =](#operator_eq)  
      
 - [operator +, -](#operator_plus_minus)  
      
 - [operator +=-=](#operator_plus_minus_eq)  
      
 - [operator * /](#operator_star)  
      
 - [operator * =, / =](#operator_star_div_eq)  
  
> [!CAUTION]
>  Ten element członkowski danych dotyczy zaawansowane sytuacjach programistycznych. Skorzystaj z wbudowanych funkcji elementów członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszych ostrzeżenia dotyczące jawne ustawienie ten element członkowski danych.  
  
##  <a name="operator_eq"></a>  COleCurrency::operator =  
 Te operatory przeciążone przypisania kopiowania wartość waluty źródła do tego `COleCurrency` obiektu.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Uwagi  
 Krótki opis każdego operatora następująco:  
  
- **Operator = (** `cySrc` **)** `CURRENCY` jest kopiowana do `COleCurrency` obiekt i jego stan jest ustawiony na prawidłowy.  
  
- **Operator = (** `curSrc` **)** wartości i stanu operand istniejące `COleCurrency` obiektu są kopiowane do tego `COleCurrency` obiektu.  
  
- **Operator = (** *varSrc* **)** Jeśli konwersja `VARIANT` wartość (lub [COleVariant](../../mfc/reference/colevariant-class.md) obiektu) walutę ( `VT_CY`) jest Operacja się powiedzie, wartość przekonwertowanego jest kopiowana do to `COleCurrency` obiekt i jego stan jest ustawiony na prawidłowy. Jeśli konwersja nie powiedzie, wartość `COleCurrency` obiekt jest ustawiony na 0 i jej stanie się nieprawidłowy.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](/windows/desktop/api/wtypes/ns-wtypes-tagcy) i [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) wpisów w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>  COleCurrency::operator +, -  
 Te operatory umożliwiają dodawania i odejmowania dwóch `COleCurrency` wartości do i od siebie nawzajem i zmienić znak `COleCurrency` wartość.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jeden z operandów jest null, stan wynikowy `COleCurrency` ma wartość null.  
  
 Jeśli operacja arytmetyczna przepełnienia, wynikowy `COleCurrency` wartość jest nieprawidłowa.  
  
 Jeśli argument jest nieprawidłowy, a drugi to nie jest to null, stan wynikowy `COleCurrency` wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>  COleCurrency::operator +=-=  
 Zezwalaj na dodawanie i odejmowanie `COleCurrency` wartości do i z tego `COleCurrency` obiektu.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jeden z operandów jest null, stan tego `COleCurrency` obiekt jest ustawiony na wartość null.  
  
 Jeśli zachodzi operacji arytmetycznej, stan tego `COleCurrency` obiekt jest ustawiony na nieprawidłową.  
  
 Jeśli jeden z operandów jest nieprawidłowa, a druga nie ma wartość null, stan tego `COleCurrency` obiekt jest ustawiony na nieprawidłową.  
  
 Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>  COleCurrency::operator \* i /  
 Pozwala na skalowanie `COleCurrency` wartości przez wartość będącą liczbą całkowitą.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `COleCurrency` operand ma wartość null, stan wynikowy `COleCurrency` ma wartość null.  
  
 Jeśli operacja arytmetyczna przepełnienie lub niedopełnienie, stan wynikowy `COleCurrency` wartość jest nieprawidłowa.  
  
 Jeśli `COleCurrency` argument operacji jest nieprawidłowy, stan wynikowy `COleCurrency` wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>  COleCurrency::operator \*=, / =  
 Pozwala to skalować `COleCurrency` wartości przez wartość będącą liczbą całkowitą.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `COleCurrency` operand ma wartość null, stan tego `COleCurrency` obiekt jest ustawiony na wartość null.  
  
 Jeśli zachodzi operacji arytmetycznej, stan tego `COleCurrency` obiekt jest ustawiony na nieprawidłową.  
  
 Jeśli `COleCurrency` argument operacji jest nieprawidłowy, stan to `COleCurrency` obiekt jest ustawiony na nieprawidłową.  
  
 Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>  COleCurrency::operator &lt; &lt;, &gt;&gt;  
 Obsługuje diagnostycznych zrzucanie i przechowywania do archiwum.  
  
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
 Wyodrębnianie ( **>>**) — operator obsługuje ładowanie z archiwum.  
  
##  <a name="operator_currency"></a>  COleCurrency::operator waluty  
 Zwraca `CURRENCY` struktury, którego wartość jest kopiowany z tym `COleCurrency` obiektu.  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="parsecurrency"></a>  COleCurrency::ParseCurrency  
 Wywołaj tę funkcję elementu członkowskiego, aby przeanalizować ciąg, który ma zostać odczytana wartość waluty.  
  
```  
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,  
    DWORD dwFlags = 0,  
    LCID lcid = LANG_USER_DEFAULT);
 
throw(CMemoryException*); 
throw(COleException*);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszCurrency*  
 Wskaźnik na ciąg zakończony znakiem null, które ma być analizowana.  
  
 *Flagidw*  
 Określa flagi dla ustawień regionalnych, prawdopodobnie następujące flagi:  
  
- LOCALE_NOUSEROVERRIDE używane domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.  
  
 *lcid*  
 Określa identyfikator ustawień regionalnych na potrzeby konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ten ciąg został pomyślnie przekonwertowany na wartość waluty, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Znaczenie znaków nienumerycznych w ciągu źródłowym używa specyfikacji język lokalny (identyfikatory ustawień regionalnych).  
  
 Omówienie wartości Identyfikatora ustawień regionalnych, zobacz [obsługi wielu języków](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).  
  
 Jeśli ten ciąg został pomyślnie przekonwertowany walutę wartość, wartość to `COleCurrency` obiekt jest ustawiony na tę wartość i jego stan prawidłowy.  
  
 Jeśli nie można przekonwertować ciągu jako wartość waluty, lub jeśli wystąpiło przepełnienie liczbowe, stan tego `COleCurrency` obiekt jest nieprawidłowy.  
  
 Jeśli Konwersja ciągu nie powiodła się z powodu błędów alokacji pamięci, ta funkcja zgłosi [CMemoryException](../../mfc/reference/cmemoryexception-class.md). W innym stanie błąd, ta funkcja zgłosi [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>  Operatory relacyjne COleCurrency  
 Porównaj dwie wartości waluty i zwracają wartość różną od zera, jeśli warunek jest prawdziwy; w przeciwnym razie 0.  
  
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
>  Wartość zwracana przez operacje szeregowania ( **<**, **\< =**, **>**, **>=**) jest niezdefiniowane, jeżeli jest w stanie oba operandy null lub jest nieprawidłowy. Operatory porównania ( `==`, `!=`) należy wziąć pod uwagę stan argumentów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>  COleCurrency::SetCurrency  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić jednostki i część ułamkową parametru to `COleCurrency` obiektu.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Parametry  
 *nUnits*, *nFractionalUnits*  
 Wskazuje jednostek i część ułamkową (w 1/10 000's) wartości, które ma być skopiowany do tego `COleCurrency` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość bezwzględna część ułamkową jest większa niż 10 000, odpowiednie dostosowania do jednostek, jak pokazano na trzecie poniższych przykładach.  
  
 Należy zauważyć, że jednostki i część ułamkową są określone przez podpisany długich wartości. Poniższe przykłady czwarta, co się stanie, jeśli parametry mają różne znaki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>  COleCurrency::SetStatus  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić stan (ważność) to `COleCurrency` obiektu.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Parametry  
 *status*  
 Nowy stan to `COleCurrency` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 *Stan* wartość parametru jest definiowana przez `CurrencyStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleCurrency` klasy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:  
  
- `COleCurrency::valid` Wskazuje, że `COleCurrency` obiekt jest prawidłowy.  
  
- `COleCurrency::invalid` Wskazuje, że `COleCurrency` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.  
  
- `COleCurrency::null` Wskazuje, że `COleCurrency` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).  
  
> [!CAUTION]
>  Ta funkcja jest zaawansowane sytuacjach programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. W większości przypadków posłuży go ustawić stan na wartość null lub nieprawidłowa. Należy pamiętać, że operator przypisania ( [operator =](#operator_eq)) i [SetCurrency](#setcurrency) skonfigurowały do obiektu, w oparciu o wartości źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleVariant](../../mfc/reference/colevariant-class.md)
