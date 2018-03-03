---
title: Klasa COleInsertDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
dev_langs:
- C++
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4638471ed199d08bb21bcf16465fe933af3a584c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coleinsertdialog-class"></a>Klasa COleInsertDialog
Używane w oknie dialogowym Wstaw obiekt OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Konstruuje `COleInsertDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|Tworzy elementu wybranego w oknie dialogowym.|  
|[COleInsertDialog::DoModal](#domodal)|Wyświetla okno dialogowe Wstaw obiekt OLE.|  
|[COleInsertDialog::GetClassID](#getclassid)|Pobiera **CLSID** skojarzone z wybranego elementu.|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Informuje, czy do rysowania elementu w postaci ikony.|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera dojścia do metaplik skojarzonych z formularzem ikony, tego elementu.|  
|[COleInsertDialog::GetPathName](#getpathname)|Pobiera pełną ścieżkę do pliku w oknie dialogowym.|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wybranego obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|Struktura typu **OLEUIINSERTOBJECT** steruje zachowaniem okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleInsertDialog` umożliwia wywołanie tego okna dialogowego. Po `COleInsertDialog` obiekt został skonstruowany, możesz użyć [m_io](#m_io) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_io` Struktura jest typu **OLEUIINSERTOBJECT**. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 Ta funkcja tworzy tylko `COleInsertDialog` obiektu.  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Tworzenie Flaga, która zawiera dowolną liczbę następujące wartości, aby można było połączyć za pomocą operatora bitowego OR:  
  
- **IOF_SHOWHELP** Określa, czy przycisk Pomoc, aby będą wyświetlane, gdy jest wywoływana w oknie dialogowym.  
  
- **IOF_SELECTCREATENEW** Określa, że Utwórz nowy przycisk radiowy wybrany zostanie początkowo wywołanego okna dialogowego. To jest ustawieniem domyślnym i nie można używać z **IOF_SELECTCREATEFROMFILE**.  
  
- **IOF_SELECTCREATEFROMFILE** Określa, że przycisk radiowy Utwórz z pliku wybrany zostanie początkowo wywołanego okna dialogowego. Nie można używać z **IOF_SELECTCREATENEW**.  
  
- **IOF_CHECKLINK** Określa, czy pole wyboru łącze będą sprawdzane początkowo wywołanego okna dialogowego.  
  
- **IOF_DISABLELINK** Określa, że pole wyboru łącza zostanie wyłączone, gdy jest wywoływana w oknie dialogowym.  
  
- **IOF_CHECKDISPLAYASICON** Określa, że pole wyboru Wyświetl jako ikonę będzie początkowo sprawdzany, będzie wyświetlana ikona bieżącego i przycisk Zmień ikonę zostanie włączona, gdy jest wywoływana w oknie dialogowym.  
  
- **IOF_VERIFYSERVERSEXIST** Określa, że okno dialogowe należy sprawdzić, czy klasy dodaje do pola listy, zapewniając, czy serwery określone w bazie danych rejestracji istnieją przed wyświetleniem okna dialogowego. Ustawienie tej flagi może znacznie obniżyć wydajność.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
##  <a name="createitem"></a>COleInsertDialog::CreateItem  
 Wywołanie tej funkcji można utworzyć obiektu typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) tylko wtedy, gdy [DoModal](#domodal) zwraca **IDOK**.  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskazuje element, który ma zostać utworzony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element został utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przydzielić `COleClientItem` obiekt przed wywołaniem tej funkcji.  
  
##  <a name="domodal"></a>COleInsertDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe Wstaw obiekt OLE.  
  
```  
virtual INT_PTR   
    DoModal();

 
INT_PTR   
    DoModal(DWORD  dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Jedna z następujących wartości:  
  
 `COleInsertDialog::DocObjectsOnly`Wstawia tylko DocObjects.  
  
 `COleInsertDialog::ControlsOnly`Wstawia tylko formantów ActiveX.  
  
 Zero wstawia DocObject ani formantu ActiveX. Tej wartości powoduje w tej samej implementacji jako pierwszego prototypu wymienionych powyżej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
-   IDOK, jeśli został pomyślnie wyświetlone okno dialogowe.  
  
-   IDCANCEL, jeśli użytkownik anulował okno dialogowe.  
  
-   IDABORT, jeśli wystąpił błąd. Jeśli zostanie zwrócony IDABORT, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_io](#m_io) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca IDOK, innego członka można wywołać funkcji można pobrać ustawień lub wprowadź informacje w oknie dialogowym przez użytkownika.  
  
##  <a name="getclassid"></a>COleInsertDialog::GetClassID  
 Wywołanie tej funkcji, aby uzyskać **CLSID** skojarzone z wybranego elementu tylko wtedy, gdy [DoModal](#domodal) zwraca **IDOK** i jest zaznaczanie **COleInsertDialog:: createNewItem**.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **CLSID** skojarzonych z wybranym elementem.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 Wywołanie tej funkcji, aby określić, czy użytkownik wybrał opcję Wyświetl zaznaczony element jako ikonę.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Metoda wymagane do renderowania obiektu.  
  
- `DVASPECT_CONTENT`Zwracany, jeśli nie zaznaczono pola wyboru Wyświetl jako ikonę.  
  
- `DVASPECT_ICON`Zwracany, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tylko wtedy, gdy funkcja [DoModal](#domodal) zwraca **IDOK**.  
  
 Aby uzyskać więcej informacji na rysunku aspekt, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury danych w zestawie Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 Wywołanie tej funkcji można uzyskać dojścia do Metaplik zawierający odpowiednikiem aspekt wybranego elementu.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do Metaplik zawierający odpowiednikiem aspekt wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę sprawdzane podczas okna dialogowego zostało odrzucone, wybierając **OK**; w przeciwnym razie **NULL**.  
  
##  <a name="getpathname"></a>COleInsertDialog::GetPathName  
 Wywołanie tej funkcji, aby uzyskać pełną ścieżkę pliku wybrany tylko wtedy, gdy [DoModal](#domodal) zwraca **IDOK** i typ wyboru nie jest **COleInsertDialog::createNewItem**.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pełna ścieżka do pliku, który został wybrany w oknie dialogowym. Jeśli typ zaznaczenia jest `createNewItem`, funkcja zwraca znaczenia `CString` w trybie wersji lub powoduje potwierdzenia w trybie debugowania.  
  
##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 Wywołanie tej funkcji można pobrać typu Wybór wybrany, gdy w oknie dialogowym Wstaw obiekt został zostanie odrzucony, wybierając **OK**.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ wybranego.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ wartości są określane przez **wybór** typ wyliczeniowy zadeklarowany w `COleInsertDialog` klasy.  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 Wykonaj krótkie opisy z następujących wartości:  
  
- **COleInsertDialog::createNewItem** wybrano Utwórz nowy przycisk radiowy.  
  
- **COleInsertDialog::insertFromFile** wybrano przycisku radiowego Utwórz z pliku i nie zaznaczono pola wyboru łącze.  
  
- **COleInsertDialog::linkToFile** wybrano przycisku radiowego Utwórz z pliku i zaznaczono pole wyboru łącza.  
  
##  <a name="m_io"></a>COleInsertDialog::m_io  
 Struktura typu **OLEUIINSERTOBJECT** służące do sterowania zachowaniem w oknie dialogowym Wstaw obiekt.  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
