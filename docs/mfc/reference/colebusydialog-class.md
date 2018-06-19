---
title: Klasa COleBusyDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b061d2cc31a67c2e6059abeaadb6062b77cacb88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374373"
---
# <a name="colebusydialog-class"></a>Klasa COleBusyDialog
Używana w oknach dialogowych OLE serwer nie odpowiada lub serwer jest zajęty.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Konstruuje `COleBusyDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|Wyświetla okno dialogowe w OLE serwer jest zajęty.|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Określa z wyborem dokonanym w oknie dialogowym.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu **OLEUIBUSY** steruje zachowaniem okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleBusyDialog` aby wywołać tych okien dialogowych. Po `COleBusyDialog` obiekt został skonstruowany, możesz użyć [m_bz](#m_bz) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_bz` Struktura jest typu **OLEUIBUSY**. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji w oknach dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog  
 Ta funkcja jedynie tworzy `COleBusyDialog` obiektu.  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *htaskBusy*  
 Dojście do zadania serwera, który jest zajęty.  
  
 *bNotResponding*  
 Jeśli **TRUE**, wywołaj okno dialogowe nie odpowiada zamiast okna dialogowego serwer jest zajęty. Treść w oknie dialogowym nie odpowiada są nieco inne niż treść w oknie dialogowym serwer jest zajęty, a przycisk Anuluj jest wyłączony.  
  
 `dwFlags`  
 Flagi tworzenia. Może zawierać zero lub więcej z następujących wartości, które są połączone z operator Alternatywy:  
  
- **BZ_DISABLECANCELBUTTON** Wyłącz przycisk Anuluj, podczas wywoływania okna dialogowego.  
  
- **BZ_DISABLESWITCHTOBUTTON** Wyłącz przycisk przełącznika do podczas wywoływania okna dialogowego.  
  
- **BZ_DISABLERETRYBUTTON** wyłącza przycisk Ponów próbę, podczas wywoływania okna dialogowego.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal).  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktury w zestawie Windows SDK.  
  
##  <a name="domodal"></a>  COleBusyDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe OLE serwer jest zajęty lub serwer nie odpowiada.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj `COleDialog::GetLastError` funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_bz](#m_bz) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, innego członka można wywołać funkcji, aby uzyskać ustawienia i informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.  
  
##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType  
 Wywołanie tej funkcji można pobrać typu Wybór wybierany przez użytkownika w oknie dialogowym serwer jest zajęty.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ wybranego.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ wartości są określane przez **wybór** typ wyliczeniowy zadeklarowany w `COleBusyDialog` klasy.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Wykonaj krótkie opisy z następujących wartości:  
  
- **COleBusyDialog::switchTo** został naciśnięty przycisk przełącznika do.  
  
- **COleBusyDialog::retry** został naciśnięty przycisk Ponów próbę.  
  
- **COleBusyDialog::callUnblocked** wywołanie, aby uaktywnić serwer jest teraz odblokowany.  
  
##  <a name="m_bz"></a>  COleBusyDialog::m_bz  
 Struktura typu **OLEUIBUSY** służące do sterowania zachowaniem okna dialogowego serwer jest zajęty.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
