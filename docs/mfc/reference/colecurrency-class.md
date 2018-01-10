---
title: Klasa COleCurrency | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d20b0f61fc7773899e671bec5b252ef2af1abf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="colecurrency-class"></a>Klasa COleCurrency
Hermetyzuje `CURRENCY` typu danych automatyzacji OLE.  
  
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
|[COleCurrency::GetStatus](#getstatus)|Pobiera stan (ważności) to `COleCurrency` obiektu.|  
|[COleCurrency::ParseCurrency](#parsecurrency)|Odczytuje **waluty** wartości z ciągu i ustawia wartość `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Ustawia wartość to `COleCurrency` obiektu.|  
|[COleCurrency::SetStatus](#setstatus)|Ustawia stan (ważności) dla tego `COleCurrency` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Kopie `COleCurrency` wartość.|  
|[operator +, -](#operator_plus_minus)|Dodaje, odejmuje i zmienia znak `COleCurrency` wartości.|  
|[operator +=-=](#operator_plus_minus_eq)|Dodaje i odejmuje `COleCurrency` wartości z tej `COleCurrency` obiektu.|  
|[operator * /](#operator_star)|Skaluje `COleCurrency` wartości przez wartość całkowitą.|  
|[operator * = / =](#operator_star_div_eq)|Skaluje to `COleCurrency` wartości przez wartość całkowitą.|  
|[Operator <<](#operator_stream)|Dane wyjściowe `COleCurrency` do wartości `CArchive` lub `CDumpContext`.|  
|[operator >>](#operator_stream)|Dane wejściowe `COleCurrency` obiekt z `CArchive`.|  
|[CURRENCY — operator](#operator_currency)|Konwertuje `COleCurrency` wartości do **waluty**.|  
|[operator ==, <, < = itp.](#colecurrency_relational_operators)|Porównuje dwa `COleCurrency` wartości.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Zawiera podstawową **waluty** dla tego `COleCurrency` obiektu.|  
|[COleCurrency::m_status](#m_status)|Zawiera informacje o stanie tego `COleCurrency` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 **COleCurrency** nie ma klasy podstawowej.  
  
 **CURRENCY** jest zaimplementowany jako 8-bajtowych, wartości całkowitej uzupełnienia do dwóch skalowana przez 10 000. Dzięki temu stałoprzecinkową liczbę 15 cyfr z lewej strony punktu dziesiętnego i 4 cyfr z prawej strony. **Waluty** — typ danych jest niezwykle użyteczne obliczeń walutowych lub wszystkie obliczenia stałoprzecinkowe których dokładność jest ważna. Jest to jeden z typów możliwych do `VARIANT` typu danych automatyzacji OLE.  
  
 **COleCurrency** implementuje również pewne podstawowe operacje arytmetyczne dla tego typu stałoprzecinkowego. Obsługiwane operacje zostały wybrane do kontrolowania zaokrąglania błędy występujące podczas stałoprzecinkowe obliczeń.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `COleCurrency`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="colecurrency"></a>COleCurrency::COleCurrency  
 Konstruuje **COleCurrency** obiektu.  
  
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
 `cySrc`  
 A **waluty** wartość ma zostać skopiowany do nowego **COleCurrency** obiektu.  
  
 `curSrc`  
 Istniejące **COleCurrency** obiekt ma zostać skopiowany do nowego **COleCurrency** obiektu.  
  
 *varSrc*  
 Istniejące **VARIANT** struktury danych (prawdopodobnie `COleVariant` obiektu) są konwertowane na wartość waluty ( `VT_CY`) i skopiowane do nowego **COleCurrency** obiektu.  
  
 `nUnits`, `nFractionalUnits`  
 Wskazuje jednostki i część ułamkowa (w 1/10 000's) wartość ma zostać skopiowany do nowego **COleCurrency** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów tworzenia nowych **COleCurrency** obiektów zainicjowany z podaną wartością. Następuje krótki opis każdego z tych konstruktorów. Jeśli nie podano inaczej, stan nowego **COleCurrency** element jest ustawiony na prawidłową.  
  
- Konstrukcje COleCurrency() **COleCurrency** obiektu równe 0 (zero).  
  
- COleCurrency (`cySrc`) tworzy **COleCurrency** obiekt z [waluty](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) wartość.  
  
- COleCurrency (`curSrc`) tworzy **COleCurrency** obiektu z istniejącego **COleCurrency** obiektu. Nowy obiekt ma ten sam status co obiekt źródłowy.  
  
- COleCurrency (`varSrc`) tworzy **COleCurrency** obiektu. Próbuje przekonwertować [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) struktury lub `COleVariant` obiektu waluty ( `VT_CY`) wartość. Jeśli ta konwersja zakończy się pomyślnie, skonwertowana wartość jest kopiowana do nowej **COleCurrency** obiektu. Jeśli nie, to wartość **COleCurrency** obiektu ma wartość zero (0) i jego stan na nieprawidłowy.  
  
- `COleCurrency(`nUnits`, `nFractionalUnits) tworzy **COleCurrency** obiektu z określonej wartości liczbowych składników. Jeśli wartość bezwzględną liczby część ułamkowa jest większa niż 10 000, odpowiedniego dostosowania do jednostek. Należy pamiętać, że jednostki i część ułamkowa są określane przez podpisany długie wartości.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) i [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) wpisów w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach pokazano skutków zero- i parametru dwa konstruktory:  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>COleCurrency::Format  
 Wywołanie tej funkcji członkowskich można utworzyć sformatowane reprezentacja wartości waluty.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Wskazuje flagi dla ustawień regionalnych. Dotyczy tylko następujące flagi waluty:  
  
- **LOCALE_NOUSEROVERRIDE** domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.  
  
 `lcid`  
 Wskazuje identyfikator ustawień regionalnych na potrzeby konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawierający wartości walutowej sformatowany.  
  
### <a name="remarks"></a>Uwagi  
 Formatuje go wartość przy użyciu specyfikacji język lokalny (identyfikatory ustawień regionalnych). Symbol waluty nie jest uwzględniony w wartości zwracanej. Jeśli stan to **COleCurrency** obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, zwracany ciąg jest określony przez zasób ciągu **IDS_INVALID_CURRENCY**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>COleCurrency::GetStatus  
 Wywołanie tej funkcji członkowskich można uzyskać stanu (ważności) z danego **COleCurrency** obiektu.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca informacje o stanie tego **COleCurrency** wartości.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest definiowana za `CurrencyStatus` wyliczany typ, który jest zdefiniowany w ramach **COleCurrency** klasy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- **COleCurrency::valid** wskazuje tego **COleCurrency** obiekt jest prawidłowy.  
  
- **COleCurrency::invalid** wskazuje tego **COleCurrency** obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleCurrency::null** wskazuje tego **COleCurrency** obiekt ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
 Stan **COleCurrency** obiektu jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli wartość jest ustawiona z **VARIANT** lub `COleVariant` wartość, która nie można przekonwertować na wartość waluty.  
  
-   Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji arytmetycznych przypisania, na przykład `+=` lub  **\* =** .  
  
-   Jeśli wartość jest nieprawidłowa została przypisana do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłową przy użyciu [SetStatus](#setstatus).  
  
 Aby uzyskać więcej informacji na operacje, które może ustawić stanu nieprawidłowego, zobacz następujące funkcje Członkowskie:  
  
- [COleCurrency](#colecurrency)  
  
- [operator =](#operator_eq)  
  
- [operator + —](#operator_plus_minus)  
  
- [operator += i-=](#operator_plus_minus_eq)  
  
- [operator * /](#operator_star)  
  
- [operator * = i / =](#operator_star_div_eq)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="m_cur"></a>COleCurrency::m_cur  
 Podstawowa [waluty](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) to struktura **COleCurrency** obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Zmiana wartości w **waluty** struktury używane przez wskaźnik zwracane przez tę funkcję zmieni wartość to **COleCurrency** obiektu. Nie zmienia stanu to **COleCurrency** obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) wejścia w zestawie Windows SDK.  
  
##  <a name="m_status"></a>COleCurrency::m_status  
 Typ elementu członkowskiego danych jest typ wyliczeniowy `CurrencyStatus`, który jest zdefiniowany w ramach **COleCurrency** klasy.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Uwagi  
 Krótki opis tych wartości stanu lista:  
  
- **COleCurrency::valid** wskazuje tego **COleCurrency** obiekt jest prawidłowy.  
  
- **COleCurrency::invalid** wskazuje tego **COleCurrency** obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleCurrency::null** wskazuje tego **COleCurrency** obiekt ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
 Stan **COleCurrency** obiektu jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli wartość jest ustawiona z **VARIANT** lub `COleVariant` wartość, która nie można przekonwertować na wartość waluty.  
  
-   Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji arytmetycznych przypisania, na przykład `+=` lub  **\* =** .  
  
-   Jeśli wartość jest nieprawidłowa została przypisana do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłową przy użyciu [SetStatus](#setstatus).  
  
 Aby uzyskać więcej informacji na operacje, które może ustawić stanu nieprawidłowego, zobacz następujące funkcje Członkowskie:  
  
- [COleCurrency](#colecurrency)  
  
- [operator =](#operator_eq)  
  
- [operator +, -](#operator_plus_minus)  
  
- [operator +=-=](#operator_plus_minus_eq)  
  
- [operator * /](#operator_star)  
  
- [operator * = / =](#operator_star_div_eq)  
  
    > [!CAUTION]
    >  Ten element członkowski danych jest zaawansowane sytuacjach programowania. Należy używać funkcji Członkowskich wbudowanego [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszego ostrzeżenia dotyczące jawne ustawienie tego elementu członkowskiego danych.  
  
##  <a name="operator_eq"></a>COleCurrency::operator =  
 Te operatory przeciążone przypisania kopiowania wartości walutowej źródła do tego **COleCurrency** obiektu.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Uwagi  
 Krótki opis każdego operatora następująco:  
  
- **Operator = (** `cySrc` **)** `CURRENCY` jest kopiowana do **COleCurrency** obiekt i jego stan jest ustawiony na prawidłową.  
  
- **Operator = (** `curSrc` **)** wartość i stan operandu istniejące **COleCurrency** obiektu są kopiowane do tego **COleCurrency** obiekt.  
  
- **Operator = (** *varSrc* **)** Jeśli konwersji `VARIANT` wartości (lub [COleVariant](../../mfc/reference/colevariant-class.md) obiektu) do waluty ( `VT_CY`) jest powodzenia skonwertowana wartość jest kopiowany do tego **COleCurrency** obiekt i jego stan jest ustawiony na prawidłową. Jeśli konwersja nie powiedzie, wartość **COleCurrency** obiektu ma wartość 0 i jego stan na nieprawidłowy.  
  
 Aby uzyskać więcej informacji, zobacz [waluty](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) i [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) wpisów w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>COleCurrency::operator +, -  
 Operatory te umożliwiają dodawania i odejmowania dwa **COleCurrency** wartości do i od siebie i zmienić znak **COleCurrency** wartości.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jeden z argumentów jest null, stan wynikowy **COleCurrency** ma wartość null.  
  
 Jeśli operacji arytmetycznej zachodzi, powstałe w ten sposób **COleCurrency** wartość jest nieprawidłowa.  
  
 Jeśli argument jest nieprawidłowy, a druga jest nie null, stan wynikowy **COleCurrency** wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>COleCurrency::operator +=-=  
 Zezwalaj na dodawanie i odejmowanie **COleCurrency** wartość do i z tego **COleCurrency** obiektu.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest jeden z argumentów, null, stan to **COleCurrency** obiekt jest ustawiony na wartość null.  
  
 Jeśli zachodzi operacji arytmetycznej, stan to **COleCurrency** obiekt jest ustawiony na nieprawidłowy.  
  
 Jeśli jeden z argumentów jest nieprawidłowa i nie ma innych wartości null, stan to **COleCurrency** obiekt jest ustawiony na nieprawidłowy.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>COleCurrency::operator * i /  
 Pozwala na skalowanie **COleCurrency** wartości przez wartość będącą liczbą całkowitą.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli **COleCurrency** argument ma wartość null, stan wynikowy **COleCurrency** ma wartość null.  
  
 Jeśli operacji arytmetycznej przepełnienie lub niedopełnienie, stan wynikowy **COleCurrency** wartość jest nieprawidłowa.  
  
 Jeśli **COleCurrency** argument jest nieprawidłowy, stan wynikowy **COleCurrency** wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>COleCurrency::operator * = / =  
 Pozwala na skalowanie to **COleCurrency** wartości przez wartość będącą liczbą całkowitą.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli **COleCurrency** argument ma wartość null, stan to **COleCurrency** obiekt jest ustawiony na wartość null.  
  
 Jeśli zachodzi operacji arytmetycznej, stan to **COleCurrency** obiekt jest ustawiony na nieprawidłowy.  
  
 Jeśli **COleCurrency** argument jest nieprawidłowy, stan to **COleCurrency** obiekt jest ustawiony na nieprawidłowy.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>COleCurrency::operator &lt; &lt;,&gt;&gt;  
 Obsługuje zrzucanie diagnostycznych i zapisywanie do archiwum.  
  
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
 Wyodrębnianie (  **>>** ) — operator obsługuje ładowanie z archiwum.  
  
##  <a name="operator_currency"></a>COleCurrency::operator waluty  
 Zwraca `CURRENCY` struktury, którego wartość jest kopiowana z to **COleCurrency** obiektu.  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="parsecurrency"></a>COleCurrency::ParseCurrency  
 Wywołanie tej funkcji Członkowskich do analizowania można odczytać wartości waluty.  
  
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
 Wskaźnik do zerem ciągu, który ma zostać przeanalizowany.  
  
 `dwFlags`  
 Wskazuje flagi dla ustawień regionalnych, prawdopodobnie następujące flagi:  
  
- **LOCALE_NOUSEROVERRIDE** domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.  
  
 `lcid`  
 Wskazuje identyfikator ustawień regionalnych na potrzeby konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie przekonwertowanie ciągu na wartość waluty, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Znaczenie liczbą znaków w ciągu źródłem używa specyfikacji język lokalny (identyfikatory ustawień regionalnych).  
  
 Aby uzyskać informacje dotyczące wartości Identyfikatora ustawień regionalnych, zobacz [obsługujące wiele języków](http://msdn.microsoft.com/en-us/47dc5add-232c-4268-b977-43e12da81ede).  
  
 Jeśli ten ciąg został pomyślnie przekonwertowany na waluty wartości, wartość to **COleCurrency** obiektu ma ustawioną tę wartość i jego stan prawidłowy.  
  
 Jeśli nie można przekonwertować ciągu na wartość waluty lub wystąpiło przepełnienie liczbowe, stan to **COleCurrency** obiektu jest nieprawidłowy.  
  
 Jeśli Konwersja ciągu nie powiodła się z powodu błędów alokacji pamięci, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md). W innych stanu błędu, funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>Operatory relacyjne COleCurrency  
 Porównuje dwie wartości waluty i zwracać niezerowy, jeśli wynikiem warunku jest PRAWDA. w przeciwnym razie 0.  
  
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
>  Wartość zwracana operacji porządkowania (  **<** ,  **\< =** ,  **>** ,  **>=** ) jest niezdefiniowana, jeśli stan którykolwiek argument operacji jest pusta lub nieprawidłowa. Operatory porównania ( `==`, `!=`) należy wziąć pod uwagę stan argumenty operacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>COleCurrency::SetCurrency  
 Wywołanie tej funkcji członkowskich można ustawić jednostki i część ułamkowa tego **COleCurrency** obiektu.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Parametry  
 `nUnits`, `nFractionalUnits`  
 Wskazuje jednostki i część ułamkowa (w 1/10 000's) wartość ma zostać skopiowany do tego **COleCurrency** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość bezwzględną liczby część ułamkowa jest większa niż 10 000, odpowiedniego dostosowania do jednostki, jak pokazano w trzecim następujące przykłady.  
  
 Należy pamiętać, że jednostki i część ułamkowa są określane przez podpisany długie wartości. Czwarty poniższych przykładach pokazano, co się stanie, jeśli parametry mają różne znaki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>COleCurrency::SetStatus  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić stan (ważności) to **COleCurrency** obiektu.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Parametry  
 *Stan*  
 Nowy stan to **COleCurrency** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 *Stan* wartość parametru jest definiowana za pomocą `CurrencyStatus` wyliczany typ, który jest zdefiniowany w **COleCurrency** klasy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- **COleCurrency::valid** wskazuje tego **COleCurrency** obiekt jest prawidłowy.  
  
- **COleCurrency::invalid** wskazuje tego **COleCurrency** obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleCurrency::null** wskazuje tego **COleCurrency** obiekt ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
    > [!CAUTION]
    >  Ta funkcja jest zaawansowane sytuacjach programowania. Ta funkcja nie ma wpływu na dane w tym obiekcie. W większości przypadków posłuży go ustawić stan o wartości null lub nieprawidłowa. Należy pamiętać, że operator przypisania ( [operatora =](#operator_eq)) i [SetCurrency](#setcurrency) ustawić stan do obiektu, w oparciu o wartości źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleVariant](../../mfc/reference/colevariant-class.md)
