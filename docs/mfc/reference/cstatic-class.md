---
title: Klasa CStatic | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs: C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8956572096240f8fbbc3a2dd116f55b67c42fc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cstatic-class"></a>Klasa CStatic
Udostępnia funkcje statyczne kontrolki systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|Konstruuje `CStatic` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatic::Create](#create)|Tworzy kontrolki statycznej systemu Windows i dołącza go do `CStatic` obiektu.|  
|[CStatic::DrawItem](#drawitem)|Należy przesłonić, aby narysować statyczną kontrolkę rysowanych przez właściciela.|  
|[CStatic::GetBitmap](#getbitmap)|Pobiera dojście mapy bitowej wcześniej ustawione z [SetBitmap](#setbitmap).|  
|[CStatic::GetCursor](#getcursor)|Pobiera dojście obrazu kursora wcześniej ustawione z [SetCursor](#setcursor).|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Pobiera dojście rozszerzony metaplik wcześniej ustawione z [SetEnhMetaFile](#setenhmetafile).|  
|[CStatic::GetIcon](#geticon)|Pobiera dojście wcześniej zestawu z ikon [SetIcon](#seticon).|  
|[CStatic::SetBitmap](#setbitmap)|Określa mapy bitowej do wyświetlenia w formancie statycznych.|  
|[CStatic::SetCursor](#setcursor)|Określa obraz kursora, który ma być wyświetlany w formancie statycznych.|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Określa rozszerzony metaplik ma być wyświetlany w formancie statycznych.|  
|[CStatic::SetIcon](#seticon)|Określa ikonę do wyświetlenia w formancie statycznych.|  
  
## <a name="remarks"></a>Uwagi  
 Statyczną kontrolkę wyświetla ciąg tekstowy, pola, prostokąt, ikona, kursor, mapy bitowej lub Ulepszony metaplik. Może służyć do etykiety, pole lub różnych innych kontrolek. Statyczną kontrolkę zwykle nie wymaga danych wejściowych i zapewnia żadnych danych wyjściowych; jednak go może powiadamiać swój element nadrzędny kliknięć myszą zostanie utworzony z **wywołania SS_NOTIFY** stylu.  
  
 Tworzenie formantu statycznych w dwóch krokach. Najpierw należy wywołać konstruktora, aby utworzyć `CStatic` obiekt, a następnie wywołaj [Utwórz](#create) funkcji członkowskiej do tworzenia kontrolki statycznej i dołącz je do `CStatic` obiektu.  
  
 W przypadku utworzenia `CStatic` obiektu w oknie dialogowym (za pośrednictwem zasób okna dialogowego), `CStatic` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CStatic` obiektów w ramach okna, może być również konieczne zniszczenia. A `CStatic` obiektu tworzone na stosie w ramach okna automatycznie zostanie zniszczony. W przypadku utworzenia `CStatic` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** obiektu zniszczyć ją po zakończeniu z nim.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="create"></a>CStatic::Create  
 Tworzy kontrolki statycznej systemu Windows i dołącza go do `CStatic` obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Określa tekst do umieszczenia w formancie. Jeśli **NULL**, tekst nie zostanie widoczne.  
  
 `dwStyle`  
 Określa styl okna kontrolki statycznej. Zastosuj dowolną kombinację [style statyczne formantu](../../mfc/reference/styles-used-by-mfc.md#static-styles) do formantu.  
  
 `rect`  
 Określa położenie i rozmiar kontrolki statycznej. Może być albo `RECT` struktury lub `CRect` obiektu.  
  
 `pParentWnd`  
 Określa `CStatic` okno nadrzędne, zwykle `CDialog` obiektu. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator kontrolki statycznej formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć `CStatic` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora `CStatic`, a następnie wywołać **Utwórz**, która tworzy kontrolki statycznej systemu Windows i dołącza go do `CStatic` obiektu.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do statycznego formantu:  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
 Jeśli użytkownik chce wyświetlać mapy bitowej, kursora, ikona lub metaplik w statyczną kontrolkę, należy zastosować jedną z następujących [style statyczne](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- **Ss_bitmap —** używały tego stylu bitmap.  
  
- **Ss_icon —** ten styl zastosowany do ikony i kursory.  
  
- **Ss_enhmetafile —** Użyj tego stylu dla rozszerzonych metaplików.  
  
 Kursory, map bitowych lub ikony można również użyć następujący styl:  
  
- **Ss_centerimage —** użyć do środka obrazu w kontrolki statycznej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>CStatic::CStatic  
 Konstruuje `CStatic` obiektu.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>CStatic::DrawItem  
 Wywoływane przez platformę, by narysować statyczną kontrolkę rysowanych przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) struktury. Struktura zawiera informacje dotyczące elementu, który ma być rysowany i typ rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję, aby zaimplementować rysunku rysowanych przez właściciela **CStatic** obiektu (formant ma styl **ss_ownerdraw —**).  
  
##  <a name="getbitmap"></a>CStatic::GetBitmap  
 Pobiera dojście mapy bitowej wcześniej ustawione z [SetBitmap](#setbitmap), która jest skojarzona z `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do bieżącego mapy bitowej, lub **NULL** Jeżeli nie ustawiono żadnych mapy bitowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>CStatic::GetCursor  
 Pobiera dojście kursora wcześniej ustawione z [SetCursor](#setcursor), która jest skojarzona z `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do bieżący kursor lub **NULL** Jeśli został ustawiony żaden kursor.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile  
 Pobiera dojście rozszerzony metaplik, ustaw wcześniej z [SetEnhMetafile](#setenhmetafile), która jest skojarzona z `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do bieżącego rozszerzony metaplik, lub **NULL** Jeżeli nie ustawiono żadnych rozszerzony metaplik.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>CStatic::GetIcon  
 Pobiera dojście wcześniej zestawu z ikon [SetIcon](#seticon), która jest skojarzona z `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do bieżącego ikony lub **NULL** Jeżeli brak ikony nie ustawiono.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>CStatic::SetBitmap  
 Kojarzy nowe mapy bitowej z kontrolki statycznej.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Dojście mapy bitowej do narysowania w kontrolki statycznej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście mapy bitowej wcześniej skojarzonego z kontrolki statycznej lub `NULL` Jeśli nie mapy bitowej nie skojarzone z kontrolki statycznej.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będzie rysowany w lewym górnym rogu i statyczne formantu będzie zmieniany rozmiar mapy bitowej.  
  
 Można użyć różnych okna i style statyczną kontrolkę, w tym te:  
  
-   Ss_bitmap — Użyj tego stylu zawsze bitmap.  
  
-   Ss_centerimage — służy do środka obrazu w kontrolki statycznej. Obraz jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, puste miejsce wokół obrazu zostanie wypełnione przez kolor pikseli w lewym górnym rogu mapy bitowej.  
  
-   Klasa zawiera MFC `CBitmap`, którego można użyć, jeśli masz więcej z obrazu mapy bitowej niż po prostu Wywołaj Win32 funkcji `LoadBitmap`. `CBitmap`, zawierającą jednego rodzaju obiektów GDI jest często używana we współpracy z `CStatic`, która jest `CWnd` klasy, która jest używana do wyświetlania obiektu graficznego jako statyczny.  
  
 `CImage`jest klasą ATL/MFC, która pozwala łatwo pracować ze map bitowych niezależnych urządzenia (DIB). Aby uzyskać więcej informacji, zobacz [CImage — klasa](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   Typowy sposób jest nadanie `CStatic::SetBitmap` obiekt GDI, który jest zwracany przez HBITMAP operator `CBitmap` lub `CImage` obiektu. Kod w tym celu jest podobny do następującego wiersza.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
Poniższy przykład tworzy dwa `CStatic` obiektów na stercie. Następnie załaduje go za pomocą mapy bitowej systemu `CBitmap::LoadOEMBitmap` , a druga z pliku przy użyciu `CImage::Load`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>CStatic::SetCursor  
 Kojarzy nowy obraz kursora z kontrolki statycznej.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parametry  
 `hCursor`  
 Dojście kursor ma być rysowany w formancie statycznych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście kursora poprzednio skojarzona z kontrolki statycznej lub **NULL** Jeśli żaden kursor nie skojarzone z kontrolki statycznej.  
  
### <a name="remarks"></a>Uwagi  
 Kursor zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będzie rysowany w lewym górnym rogu i statyczne formantu będzie zmieniany rozmiar kursora.  
  
 Można użyć różnych okna i style statyczne formantu, takie jak następujące:  
  
- **Ss_icon —** zawsze używały tego stylu dla ikony i kursory.  
  
- **Ss_centerimage —** używany do środka w kontrolki statycznej. Obraz jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, puste miejsce wokół obrazu zostaną wypełnione kolorem tła kontrolki statycznej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile  
 Kojarzy nowy obraz rozszerzony metaplik z kontrolki statycznej.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Parametry  
 `hMetaFile`  
 Dojście rozszerzony metaplik jest narysowanie w kontrolki statycznej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście rozszerzony metaplik poprzednio skojarzona z kontrolki statycznej lub **NULL** Jeśli nie rozszerzony metaplik nie skojarzony z kontrolką statycznych.  
  
### <a name="remarks"></a>Uwagi  
 Rozszerzony metaplik zostanie automatycznie narysowana kontrolki statycznej. Rozszerzony metaplik jest skalowane w celu dopasowania go do rozmiaru kontrolki statycznej.  
  
 Można użyć różnych okna i style statyczne formantu, takie jak następujące:  
  
- **Ss_enhmetafile —** zawsze używały tego stylu dla rozszerzonych metaplików.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>CStatic::SetIcon  
 Kojarzy nowy obraz ikony z kontrolki statycznej.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Dojście ikonę, aby być rysowany w kontrolki statycznej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście ikona poprzednio skojarzona z kontrolki statycznej lub **NULL** jeśli skojarzony z kontrolką statycznych nie ma ikony.  
  
### <a name="remarks"></a>Uwagi  
 Ikona zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będzie rysowany w lewym górnym rogu i statyczne formantu będzie zmieniany do rozmiaru ikony.  
  
 Można użyć różnych okna i style statyczne formantu, takie jak następujące:  
  
- **Ss_icon —** zawsze używały tego stylu dla ikony i kursory.  
  
- **Ss_centerimage —** używany do środka w kontrolki statycznej. Obraz jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, puste miejsce wokół obrazu zostaną wypełnione kolorem tła kontrolki statycznej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)
