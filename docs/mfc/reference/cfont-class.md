---
title: "Cfont — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
dev_langs: C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65c1fd6d86c153881f8674732db2b61edcfab8cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cfont-class"></a>Cfont — klasa
Hermetyzuje czcionkę interfejsu (GDI) systemu Windows grafiki urządzenia i udostępnia funkcje Członkowskie do manipulowania czcionki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|Konstruuje `CFont` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|Inicjuje `CFont` o określonej charakterystyce.|  
|[CFont::CreateFontIndirect](#createfontindirect)|Inicjuje `CFont` obiektu o charakterystyce podany w `LOGFONT` struktury.|  
|[CFont::CreatePointFont](#createpointfont)|Inicjuje `CFont` o określonej wysokości, mierzony w dziesiąte części punktu i krój czcionki.|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Taki sam jak `CreateFontIndirect` z tą różnicą, że wysokość czcionki jest mierzony w dziesiąte części punkt, a nie jednostek logicznych.|  
|[CFont::FromHandle](#fromhandle)|Zwraca wskaźnik do `CFont` obiektu, gdy Windows **HFONT**.|  
|[CFont::GetLogFont](#getlogfont)|Wypełnia `LOGFONT` informacji o logicznych czcionki dołączony do `CFont` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HFONT CFont::operator](#operator_hfont)|Zwraca dojście czcionek GDI systemu Windows jest dołączony do `CFont` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CFont` obiektów, utworzyć `CFont` obiektu i dołączyć czcionki systemu Windows do niego z [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), lub [CreatePointFontIndirect](#createpointfontindirect), a następnie użyć funkcji elementów członkowskich obiektu do manipulowania czcionki.  
  
 `CreatePointFont` i `CreatePointFontIndirect` funkcje są często łatwiejsze niż w `CreateFont` lub `CreateFontIndirect` ponieważ są one automatycznie, czy konwersji wysokość czcionki z rozmiar czcionki do jednostek logicznych.  
  
 Aby uzyskać więcej informacji na temat `CFont`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cfont"></a>CFont::CFont  
 Konstruuje `CFont` obiektu.  
  
```  
CFont();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wynikowy musi zostać zainicjowany z `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, lub `CreatePointFontIndirect` zanim będzie można go używać.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>CFont::CreateFont  
 Inicjuje `CFont` obiektu o określonej charakterystyce.  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>Parametry  
 `nHeight`  
 Określa żądaną wysokość (w jednostkach logicznych) czcionki. Zobacz `lfHeight` członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)struktury w zestawie SDK systemu Windows, aby uzyskać opis. Wartość bezwzględna `nHeight` nie może przekraczać 16 384 jednostki urządzenia po konwersji. Wszystkie wysokość porównań mapowania czcionki wyszukuje największą czcionki, która nie przekracza rozmiar żądanej lub najmniejszy wszystkie czcionki o większym żądany rozmiar.  
  
 `nWidth`  
 Określa średnią szerokość (w jednostkach logicznych) znaków w czcionce. Jeśli `nWidth` wynosi 0, współczynnik proporcji urządzenia będą dopasowywane współczynnik proporcji digitization dostępnych czcionek, aby znaleźć najlepsze dopasowanie, który jest określany przez wartość bezwzględna różnicy.  
  
 `nEscapement`  
 Określa kąt (w jednostkach stopnia 0,1) między wektor escapement i powierzchni wyświetlania osi x. Wektor escapement jest przekreślonym źródła pierwszy i ostatni znak w wierszu. Kąt jest mierzony przeciwnie osi x. Zobacz `lfEscapement` element członkowski w `LOGFONT` struktury w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
 `nOrientation`  
 Określa kąt (w jednostkach stopnia 0,1) między linii bazowej znaku i osi x. Kąt jest mierzony przeciwnie osi x dla współrzędnych systemów, w których kierunku y jest dół i w prawo z osi x dla współrzędnych systemy, w których działa kierunku y.  
  
 `nWeight`  
 Określa grubość czcionki (w pikselach połączone na 1000). Zobacz `lfWeight` element członkowski w `LOGFONT` struktury w zestawie SDK systemu Windows, aby uzyskać więcej informacji. Wartości opisane są przybliżone; wygląd rzeczywisty zależy od kroju pisma. Niektóre czcionki mają tylko `FW_NORMAL`, `FW_REGULAR`, i `FW_BOLD` wagi. Jeśli `FW_DONTCARE` określono wagi domyślny jest używany.  
  
 `bItalic`  
 Określa, czy czcionka jest kursywą.  
  
 `bUnderline`  
 Określa, czy czcionka jest podkreślona.  
  
 `cStrikeOut`  
 Określa, czy są wykreślić, znaków w czcionce. Określa czcionkę przekreślenia, jeśli ustawiono wartość różną od zera.  
  
 `nCharSet`  
 Określa czcionkę znak setSee `lfCharSet` element członkowski w `LOGFONT` struktury w zestawie SDK systemu Windows, aby uzyskać listę wartości.  
  
 Zbiór znaków OEM jest zależny od systemu.  
  
 Czcionki z innych zestawów znaków może istnieć w systemie. Aplikacja, która używa czcionki z zestawem znaków nieznany nie wolno próbować tłumaczenie i interpretowania ciągów, które mają być renderowane przy tym czcionki. Zamiast tego ciągi powinny zostać przekazane bezpośrednio do wyjścia sterownika urządzenia.  
  
 Mapowania czcionek nie używa `DEFAULT_CHARSET` wartość. Aby umożliwić nazwę i rozmiar czcionki do opisywania pełni logicznej czcionki tej wartości można użyć aplikacji. Jeśli czcionki o określonej nazwie nie istnieje, można zastąpić czcionki z każdego zestawu znaków określonej czcionki. Aby uniknąć nieoczekiwanych wyników, aplikacje powinny używać `DEFAULT_CHARSET` wartość oszczędnie.  
  
 `nOutPrecision`  
 Określa dokładność żądanego wyniku. Dane wyjściowe precyzji Określa, jak blisko dane wyjściowe muszą być zgodne żądanej czcionki wysokość, szerokość znaku orientacji, escapement i wysokość. Zobacz `lfOutPrecision` element członkowski w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości oraz dodatkowe informacje.  
  
 `nClipPrecision`  
 Określa dokładność żądaną wycinka. Dokładność wycinka definiuje sposób obcina znaki, które są częściowo spoza obszaru przycinania. Zobacz `lfClipPrecision` element członkowski w `LOGFONT` struktury w zestawie SDK systemu Windows, aby uzyskać listę wartości.  
  
 Aby używać osadzonych tylko do odczytu, należy określić aplikację `CLIP_ENCAPSULATE`.  
  
 Uzyskanie spójnej obrotu urządzenia, TrueType i czcionki wektorowe aplikacji można używać operatora OR połączyć `CLIP_LH_ANGLES` wartości z żadnym innym `nClipPrecision` wartości. Jeśli `CLIP_LH_ANGLES` ustawiono bit, obrotu dla wszystkich czcionek zależy od tego, czy dla leworęcznych ma orientację układu współrzędnych lub praworęczny. (Aby uzyskać więcej informacji na temat orientację systemów współrzędnych, zobacz opis `nOrientation` parametru.) Jeśli `CLIP_LH_ANGLES` jest nieustawiony, czcionki urządzenia zawsze Obróć w lewo, ale obrót czcionki jest zależna od orientację układu współrzędnych.  
  
 `nQuality`  
 Określa jakość czcionki, który definiuje sposób dokładnie interfejs GDI musi próbował dopasować atrybuty logiczne czcionki do tych rzeczywiste czcionki fizycznych. Zobacz `lfQuality` element członkowski w `LOGFONT` struktury w zestawie SDK systemu Windows, aby uzyskać listę wartości.  
  
 `nPitchAndFamily`  
 Określa gęstość i rodzinę czcionek. Zobacz `lfPitchAndFamily` element członkowski w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości oraz dodatkowe informacje.  
  
 `lpszFacename`  
 A `CString` lub wskaźnik do zerem ciąg określający nazwę krój czcionki. Długość tego ciągu nie może przekraczać 30 znaków. Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) funkcji można używać wyliczyć wszystkie aktualnie dostępne czcionki. Jeśli `lpszFacename` jest `NULL`, interfejs GDI używa krój niezależnych od urządzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać czcionkę czcionki dla dowolnego kontekstu urządzenia.  
  
 `CreateFont` Funkcja nie powoduje utworzenia nowego czcionek GDI systemu Windows. Go jedynie wybiera najlepsze dopasowanie z fizycznego czcionek dostępnych do interfejs GDI.  
  
 Aplikacje mogą używać domyślnych ustawień dla większości parametrów podczas tworzenia logicznego czcionki. Parametry, które powinien zawsze mieć określone wartości są `nHeight` i `lpszFacename`. Jeśli `nHeight` i `lpszFacename` nie są ustawione przez aplikację, logiczną czcionki, która jest tworzona jest zależny od urządzenia.  
  
 Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreateFont` funkcji, należy użyć `CDC::SelectObject` aby wybrać inną czcionkę w kontekście urządzenia, następnie usuń `CFont` obiekt, który nie jest już potrzebne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>CFont::CreateFontIndirect  
 Inicjuje `CFont` obiektu o charakterystyce podany w [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)struktury.  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogFont`  
 Wskazuje `LOGFONT` strukturę, która definiuje właściwości logicznej czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać czcionkę jako bieżącą czcionkę dla każdego urządzenia.  
  
 Tę czcionkę o cechach określone w [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury. Po wybraniu czcionkę przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcji członkowskiej mapowania czcionek GDI próbuje dopasować logicznej czcionki z istniejących czcionki fizycznych. Jeśli mapowania czcionki nie może znaleźć dokładnego dopasowania dla logicznego czcionki, zapewnia alternatywny czcionki, którego charakterystyka dopasowywać jako wiele żądanej właściwości, jak to możliwe.  
  
 Gdy nie są już potrzebne `CFont` obiekt utworzony przez `CreateFontIndirect` funkcji, należy użyć `CDC::SelectObject` aby wybrać inną czcionkę w kontekście urządzenia, następnie usuń `CFont` obiekt, który nie jest już potrzebne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>CFont::CreatePointFont  
 Ta funkcja zapewnia prosty sposób utworzyć czcionkę określony krój czcionki i rozmiar w punktach.  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nPointSize`  
 Żądana wysokość czcionki w dziesiąte części punktu. (Na przykład przekazać 120 żądania czcionki 12 punktów).  
  
 `lpszFaceName`  
 A `CString` lub wskaźnik do zerem ciąg określający nazwę krój czcionki. Długość tego ciągu nie może przekraczać 30 znaków. Windows **EnumFontFamilies** funkcji można używać wyliczyć wszystkie aktualnie dostępne czcionki. Jeśli `lpszFaceName` jest **NULL**, interfejs GDI używa krój niezależnych od urządzenia.  
  
 `pDC`  
 Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiekt służący do konwertowania wysokość w `nPointSize` do jednostek logicznych. Jeśli **NULL**, kontekst urządzenia ekranu służy do konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Automatycznie konwertuje wysokość w `nPointSize` do jednostek logicznych przy użyciu `CDC` obiekt wskazywany przez `pDC`.  
  
 Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreatePointFont` funkcji, najpierw wybierz czcionkę poza kontekstem urządzenia, a następnie usuń `CFont` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 Ta funkcja jest taka sama jak [CreateFontIndirect](#createfontindirect) z tą różnicą, że **lfHeight** członkiem `LOGFONT` jest interpretowana w dziesiąte części jednostki punktu, a nie urządzeń.  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogFont`  
 Wskazuje [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) strukturę, która definiuje właściwości logicznej czcionki. **LfHeight** członkiem `LOGFONT` struktury jest mierzony w dziesiąte części punkt, a nie jednostek logicznych. (Na przykład ustawić **lfHeight** do 120 żądania czcionki 12 punktów.)  
  
 `pDC`  
 Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiekt służący do konwertowania wysokość w **lfHeight** do jednostek logicznych. Jeśli **NULL**, kontekst urządzenia ekranu służy do konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powoduje automatyczną konwersję wysokość w **lfHeight** do jednostek logicznych przy użyciu `CDC` obiekt wskazywany przez `pDC` przed przekazaniem `LOGFONT` struktury do systemu Windows.  
  
 Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreatePointFontIndirect` funkcji, najpierw wybierz czcionkę poza kontekstem urządzenia, a następnie usuń `CFont` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CFont::FromHandle  
 Zwraca wskaźnik do `CFont` obiektu, gdy **HFONT** uchwyt do obiektu czcionek GDI systemu Windows.  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>Parametry  
 `hFont`  
 **HFONT** dojścia do czcionki systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CFont` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CFont` obiekt nie jest już dołączony do uchwytu, tymczasowej `CFont` obiekt jest tworzony i dołączyć. To tymczasowe `CFont` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w czasu grafiki wszystkie tymczasowe obiekty zostaną usunięte. Innymi słowy to jest tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>CFont::GetLogFont  
 Wywołanie tej funkcji, aby pobrać kopię `LOGFONT` struktury `CFont`.  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>Parametry  
 *pLogFont*  
 Wskaźnik do [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury otrzymywanie informacji czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się powodzeniem, w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>HFONT CFont::operator  
 Użyj tego operatora, można pobrać uchwytu Windows GDI czcionki dołączony do `CFont` obiektu.  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt obiektu czcionek GDI systemu Windows jest dołączony do `CFont` przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ ten operator jest automatycznie używany podczas konwersji z `CFont` do [czcionki i tekst](http://msdn.microsoft.com/library/windows/desktop/dd144819), można przekazać `CFont` obiektów do funkcji, które oczekują **HFONT**s.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)



