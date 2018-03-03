---
title: Klasa CEditView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs:
- C++
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78aa34f1790b2e86dae183b96c88b4ed35483927
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ceditview-class"></a>Klasa CEditView
Typ widoku klasy, która udostępnia funkcje systemu Windows formantu edycyjnego i może służyć do implementowania prostego edytora tekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|Tworzy obiekt typu `CEditView`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|Wyszukuje ciąg w tekście.|  
|[CEditView::GetBufferLength](#getbufferlength)|Pobiera długość buforu znaków.|  
|[CEditView::GetEditCtrl](#geteditctrl)|Zapewnia dostęp do `CEdit` część `CEditView` obiektu (pole edycji systemu Windows).|  
|[CEditView::GetPrinterFont](#getprinterfont)|Pobiera bieżącą czcionkę drukarki.|  
|[CEditView::GetSelectedText](#getselectedtext)|Pobiera aktualnie zaznaczonego tekstu.|  
|[CEditView::LockBuffer](#lockbuffer)|Blokuje buforu.|  
|[CEditView::PrintInsideRect](#printinsiderect)|Renderuje tekst wewnątrz danej prostokąta.|  
|[CEditView::SerializeRaw](#serializeraw)|Serializuje `CEditView` obiektu na dysku jako tekst raw.|  
|[CEditView::SetPrinterFont](#setprinterfont)|Ustawia nowej czcionki drukarki.|  
|[CEditView::SetTabStops](#settabstops)|Ustawia tabulatory ekranu i drukowania.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|Umożliwia odblokowanie buforu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie ciągu tekstowego.|  
|[CEditView::OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia ciągu nowe parametry.|  
|[CEditView::OnReplaceSel](#onreplacesel)|Zamienia bieżące zaznaczenie.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|Wywoływane, gdy Operacja find nie powiedzie się do dopasowania dalsze tekst.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|Domyślny styl dla obiektów typu **CEditView.**|  
  
## <a name="remarks"></a>Uwagi  
 `CEditView` Klasy oferuje następujące dodatkowe funkcje:  
  
-   Drukowanie.  
  
-   Znajdź i Zamień.  
  
 Ponieważ klasa `CEditView` jest pochodną klasy `CView`, obiektów klasy `CEditView` może być używany z dokumentów i szablonów dokumentów.  
  
 Każdy `CEditView` tekstu formantu jest przechowywana w obiekcie własnej pamięci globalnej. Aplikacja może zawierać dowolną liczbę `CEditView` obiektów.  
  
 Tworzenie obiektów typu `CEditView` okno edycji o dodatkowe funkcje wymienione powyżej, lub jeśli chcesz, aby funkcje prostego edytora tekstu. A `CEditView` obiektu może być obszaru klienckiego całe okno. Pochodzi własnych klas z `CEditView` do dodawania lub modyfikowania podstawowych funkcji lub zadeklarować klas, które można dodać do szablonu dokumentu.  
  
 Domyślna implementacja klasy `CEditView` obsługuje następujące polecenia: **id_edit_select_all —**, **id_edit_find —**, **id_edit_replace —**, **Id_edit_repeat —**, i **id_file_print —**.  
  
 Domyślny limit znaków `CEditView` jest (1024 \* 1024-1 = 1048575). Można to zmienić, wywołując **EM_LIMITTEXT** formantu edycyjnego funkcji podstawowych. Jednak ograniczenia są różne w zależności od systemu operacyjnego i typ edytować formantu (jeden lub wielowierszowe). Aby uzyskać więcej informacji o tych ograniczeń, zobacz [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Aby zmienić ten limit formantu, należy zastąpić `OnCreate()` działać w ramach Twojej `CEditView` klasy i Wstaw następujący wiersz kodu:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 Obiekty typu `CEditView` (lub typy pochodzące z `CEditView`) ma następujące ograniczenia:  
  
- `CEditView`nie implementuje true zostanie wyświetlony to edycji (WYSIWYG). W przypadku, gdy istnieje wybór między czytelności na ekranie i dopasowania wydruku `CEditView` zdecyduje się na czytelność ekranu.  
  
- `CEditView`można wyświetlić tekst w jednej czcionki. Formatowanie znaków specjalnych nie jest obsługiwana. Zawiera opis klasy [cricheditview —](../../mfc/reference/cricheditview-class.md) dla więcej możliwości.  
  
-   Ilość tekstu `CEditView` może zawierać jest ograniczona. Ograniczenia są takie same jak w przypadku `CEdit` formantu.  
  
 Aby uzyskać więcej informacji na temat `CEditView`, zobacz [pochodnych widoku klasy dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 Tworzy obiekt typu `CEditView`.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, należy wywołać [CWnd::Create](../../mfc/reference/cwnd-class.md#create) działać, zanim będzie można użyć kontrolki edycji. Jeśli pochodzi z klasy `CEditView` i dodaj go do szablonu, za pomocą `CWinApp::AddDocTemplate`, struktura wywołuje zarówno ten konstruktor i **Utwórz** funkcji.  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 Domyślny styl zawiera `CEditView` obiektu.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>Uwagi  
 Przekaż ten statyczny element członkowski jako `dwStyle` parametr **Utwórz** aby otrzymać domyślny styl `CEditView` obiektu.  
  
##  <a name="findtext"></a>CEditView::FindText  
 Wywołanie `FindText` funkcja wyszukiwania `CEditView` buforu tekstu obiektu.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który ma zostać odnaleziona.  
  
 `bNext`  
 Określa kierunek wyszukiwania. Jeśli **TRUE**, jest skierowany wyszukiwania do końca buforu. Jeśli **FALSE**, kierunek wyszukiwania jest początku buforu.  
  
 `bCase`  
 Określa, czy wyszukiwanie uwzględnia wielkość liter. Jeśli **TRUE**, wyszukiwanie jest rozróżniana wielkość liter. Jeśli **FALSE**, wyszukiwanie nie jest uwzględniana wielkość liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zostanie znaleziony tekst; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wyszukuje tekst w buforze dla tekstu określonego przez `lpszFind`, rozpoczynając od bieżącego zaznaczenia w kierunku określony przez `bNext`oraz o wielkości liter, określony przez `bCase`. Jeśli tekst zostanie znaleziony, ustawia zaznaczenie znaleziony tekst i zwraca wartość różną od zera. Jeśli tekst nie zostanie znaleziony, funkcja zwraca wartość 0.  
  
 Zwykle nie trzeba wywołać `FindText` działać, chyba że nadpiszesz `OnFindNext`, które wywołuje `FindText`.  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 Wywołanie tej funkcji elementu członkowskiego w celu uzyskania liczby znaków obecnie w formancie edycyjnym buforze nie włącznie z terminatorem null.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu w buforze.  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 Wywołanie `GetEditCtrl` można pobrać odwołania do kontrolki edycji używane przez widok edycji.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CEdit` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ten formant jest typu [CEdit](../../mfc/reference/cedit-class.md), więc można manipulować kontrolki edycji systemu Windows bezpośrednio przy użyciu `CEdit` funkcji elementów członkowskich.  
  
> [!CAUTION]
>  Przy użyciu `CEdit` obiektów, Zmień stan podstawowej systemu Windows można edytować kontrolkę. Na przykład nie należy zmieniać ustawień kartę za pomocą [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) działać, ponieważ `CEditView` buforuje te ustawienia do użycia zarówno w formancie edycyjnym w drukowania. Zamiast tego należy użyć [CEditView::SetTabStops](#settabstops).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 Wywołanie `GetPrinterFont` otrzymywać wskaźnik do [cfont —](../../mfc/reference/cfont-class.md) obiektu, który opisuje bieżącą czcionkę drukarki.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CFont` obiekt, który określa bieżącą czcionkę drukarki; **NULL** Jeśli czcionki drukarki nie została ustawiona. Wskaźnik mogą być tymczasowe i nie powinny być przechowywane do późniejszego użycia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli czcionki drukarki nie została ustawiona, domyślne zachowanie drukowanie `CEditView` klasy jest drukowanie przy użyciu tej samej czcionki używany do wyświetlania.  
  
 Ta funkcja służy do określenia bieżącej czcionki drukarki. Jeśli nie jest czcionka żądaną drukarki, użyj [CEditView::SetPrinterFont](#setprinterfont) je zmienić.  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 Wywołanie `GetSelectedText` do zaznaczonego tekstu do skopiowania `CString` obiektu do końca zaznaczenia lub znak poprzedzający pierwszy znak powrotu karetki w zaznaczeniu.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strResult`  
 Odwołanie do `CString` obiektu, który ma otrzymać zaznaczony tekst.  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 Wywołanie tej funkcji Członkowskich uzyskać wskaźnik do buforu. Bufor nie powinien być modyfikowany.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do kontrolki edycji buforu.  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 Wyszukuje tekst w buforze dla tekstu określonego przez `lpszFind`, w tym kierunku określony przez `bNext`, o wielkości liter, określony przez `bCase`.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który ma zostać odnaleziona.  
  
 `bNext`  
 Określa kierunek wyszukiwania. Jeśli **TRUE**, jest skierowany wyszukiwania do końca buforu. Jeśli **FALSE**, kierunek wyszukiwania jest początku buforu.  
  
 `bCase`  
 Określa, czy wyszukiwanie uwzględnia wielkość liter. Jeśli **TRUE**, wyszukiwanie jest rozróżniana wielkość liter. Jeśli **FALSE**, wyszukiwanie nie jest uwzględniana wielkość liter.  
  
### <a name="remarks"></a>Uwagi  
 Wyszukiwanie rozpoczyna się od początku bieżącego zaznaczenia i odbywa się za pośrednictwem wywołania [ciąg FindText](#findtext). W implementacji domyślnej `OnFindNext` wywołania [OnTextNotFound](#ontextnotfound) Jeśli tekst nie zostanie znaleziony.  
  
 Zastąpienie `OnFindNext` zmienić sposób `CEditView`-pochodnej obiektu wyszukiwania tekstu. `CEditView`wywołania `OnFindNext` gdy użytkownik wybierze przycisk Znajdź następny standardowe okno dialogowe Znajdź.  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`wywołania `OnReplaceAll` gdy użytkownik wybierze przycisk Zastąp wszystkie standardowe okno dialogowe Zamień.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który ma zostać odnaleziona.  
  
 `lpszReplace`  
 Tekst, który zastępuje tekst wyszukiwania.  
  
 `bCase`  
 Określa, czy wyszukiwanie uwzględnia wielkość liter. Jeśli **TRUE**, wyszukiwanie jest rozróżniana wielkość liter. Jeśli **FALSE**, wyszukiwanie nie jest uwzględniana wielkość liter.  
  
### <a name="remarks"></a>Uwagi  
 `OnReplaceAll`Wyszukiwanie tekstu w buforze dla tekstu określonego przez `lpszFind`, o wielkości liter, określony przez `bCase`. Wyszukiwanie rozpoczyna się na początku bieżącego zaznaczenia. Zawsze wyszukiwany tekst zostanie znaleziony, ta funkcja zastępuje to wystąpienie tekstu tekstu określonego przez `lpszReplace`. Wyszukiwanie odbywa się za pośrednictwem wywołania [ciąg FindText](#findtext). W implementacji domyślnej [OnTextNotFound](#ontextnotfound) jest wywoływana, gdy tekst nie zostanie znaleziony.  
  
 Jeśli bieżące zaznaczenie nie odpowiada `lpszFind`, zaznaczenie jest aktualizowana w celu pierwszego wystąpienia tekstu określonego przez `lpszFind` i zamiany nie jest wykonywana. Dzięki temu użytkownikowi potwierdzić, że jest to chcą robić, jeśli zaznaczenie jest niezgodna z tekst do zastąpienia.  
  
 Zastąpienie `OnReplaceAll` zmienić sposób `CEditView`-obiektu pochodnego zamienia tekst.  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`wywołania `OnReplaceSel` użytkownik wybrał przycisk Zamień w oknie dialogowym Zamień standardowa.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który ma zostać odnaleziona.  
  
 `bNext`  
 Określa kierunek wyszukiwania. Jeśli **TRUE**, jest skierowany wyszukiwania do końca buforu. Jeśli **FALSE**, kierunek wyszukiwania jest początku buforu.  
  
 `bCase`  
 Określa, czy wyszukiwanie uwzględnia wielkość liter. Jeśli **TRUE**, wyszukiwanie jest rozróżniana wielkość liter. Jeśli **FALSE**, wyszukiwanie nie jest uwzględniana wielkość liter.  
  
 `lpszReplace`  
 Tekst, który ma zastąpić znaleziony tekst.  
  
### <a name="remarks"></a>Uwagi  
 Po wymianie zaznaczenie, ta funkcja wyszukuje tekst w buforze na następne wystąpienie tekstu określonego przez `lpszFind`, w kierunku określony przez `bNext`, o wielkości liter, określony przez `bCase`. Wyszukiwanie odbywa się za pośrednictwem wywołania [ciąg FindText](#findtext). Jeśli tekst nie zostanie znaleziony, [OnTextNotFound](#ontextnotfound) jest wywoływana.  
  
 Zastąpienie `OnReplaceSel` zmienić sposób `CEditView`-obiektu pochodnego zastępuje zaznaczonego tekstu.  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 Przesłonić tę funkcję, aby zmienić domyślną implementację, która wywołuje funkcję Windows **MessageBeep**.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który ma zostać odnaleziona.  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 Wywołanie `PrintInsideRect` drukowanie tekstu w prostokącie określonego przez *rectLayout*.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia drukarki.  
  
 *rectLayout*  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [struktura RECT](../../mfc/reference/rect-structure1.md) Określanie prostokąt, w którym ma być renderowany tekst.  
  
 `nIndexStart`  
 Indeks pierwszego znaku do renderowania buforu.  
  
 `nIndexStop`  
 Indeks w buforze znaków po ostatnim znaku do renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks następny znak do wydrukowania (to znaczy znak po ostatnim znaku renderowane).  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CEditView` formant nie ma styl **es_autohscroll —**, tekst zawija się w prostokącie renderowania. Jeśli formant ma styl **es_autohscroll —**, zostanie obcięta na prawej krawędzi prostokąta.  
  
 **Rect.bottom** elementu *rectLayout* obiektu zostanie zmieniona tak, aby wymiary prostokąta zdefiniować część oryginalnego prostokąt, który jest zajęta przez tekst.  
  
##  <a name="serializeraw"></a>CEditView::SerializeRaw  
 Wywołanie `SerializeRaw` mają `CArchive` obiekt odczytu lub zapisu tekst `CEditView` obiektu do pliku tekstowego.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 Odwołanie do `CArchive` obiekt, który przechowuje tekst serializacji.  
  
### <a name="remarks"></a>Uwagi  
 `SerializeRaw`różni się od `CEditView`w wewnętrznej implementacji `Serialize` w tym odczytuje i zapisuje tylko tekst bez poprzedzających opis obiektu danych.  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 Wywołanie `SetPrinterFont` do ustawienia czcionki drukarki do czcionki określony przez `pFont`.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Wskaźnik do obiektu typu `CFont`. Jeśli **NULL**, czcionka używana na potrzeby drukowania jest oparta na wyświetlanie czcionek.  
  
### <a name="remarks"></a>Uwagi  
 Widok, aby zawsze używać określonej czcionki do drukowania, należy włączyć wywołanie `SetPrinterFont` w swojej klasy `OnPreparePrinting` funkcji. Ta wirtualnych funkcja jest wywoływana przed wystąpieniem drukowanie, więc zmiana czcionki ma miejsce przed jego zawartość jest drukowana.  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 Wywołanie tej funkcji do ustawiania tabulatorów używany do wyświetlania i drukowania.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `nTabStops`  
 Szerokość każdego tabulatora, w jednostkach okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Jest obsługiwany tylko jeden szerokość tabulatora. ( `CEdit` obiekty obsługują wiele szerokości karty.) Szerokości są w jednostkach okna dialogowego, które równa jednej czwartej szerokość znaku średni (oparte na wielkie i małe litery alfabetu tylko) czcionki używany w czasie drukowania lub wyświetlania. Nie należy używać `CEdit::SetTabStops` ponieważ `CEditView` musi buforowania wartości tabulatora.  
  
 Ta funkcja modyfikuje tylko karty obiektu, dla którego jest wywoływana. Aby zmienić na karcie zatrzymuje dla każdego `CEditView` obiektów w aplikacji, wywołaj każdego obiektu `SetTabStops` funkcji.  
  
### <a name="example"></a>Przykład  
 Fragmentu kodu ustawia tabulatorów w formancie do każdego znaku czwarty mierząc dokładnie czcionkę, której używa kontrolki.  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 Wywołanie tej funkcji Członkowskich, aby odblokować buforu.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `UnlockBuffer` po zakończeniu przy użyciu wskaźnika zwrócony przez [LockBuffer](#lockbuffer).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Cdocument — klasa](../../mfc/reference/cdocument-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
