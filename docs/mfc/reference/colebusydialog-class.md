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
ms.openlocfilehash: f5b99266d465629853361c07ea16f9ae620b0e24
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210831"
---
# <a name="colebusydialog-class"></a>Klasa COleBusyDialog
Używane dla okien dialogowych OLE serwer nie odpowiada lub serwer jest zajęty.  
  
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
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Określa, z wyborem dokonanym w oknie dialogowym.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY kontrolujące zachowanie okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleBusyDialog` gdy zachodzi potrzeba wywołania tych okien dialogowych. Po `COleBusyDialog` obiekt został skonstruowany, możesz użyć [m_bz](#m_bz) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_bz` Struktury jest typu OLEUIBUSY. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktury w zestawie Windows SDK.  
  
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
 Ta funkcja tylko tworzy `COleBusyDialog` obiektu.  
  
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
 W przypadku opcji TRUE Wywołaj okno dialogowe nie odpowiada zamiast okna dialogowego serwer jest zajęty. Treść w oknie dialogowym nie odpowiada są nieco inne niż treść serwer jest zajęty w oknie dialogowym, a przycisk Anuluj jest wyłączony.  
  
 *Flagidw*  
 Flagi tworzenia. Może zawierać zero lub więcej z następujących wartości, które są połączone za pomocą operatora bitowego OR:  
  
- Podczas wywoływania okno dialogowe, BZ_DISABLECANCELBUTTON wyłączyć przycisk Anuluj.  
  
- Wyłącz BZ_DISABLESWITCHTOBUTTON Przełącz do przycisku podczas wywoływania okno dialogowe.  
  
- Podczas wywoływania okno dialogowe, BZ_DISABLERETRYBUTTON wyłączyć przycisk Ponów próbę.  
  
 *pParentWnd*  
 Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne z obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal).  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktury w zestawie Windows SDK.  
  
##  <a name="domodal"></a>  COleBusyDialog::DoModal  
 Wywołaj tę funkcję, aby wyświetlić okno dialogowe OLE serwer jest zajęty lub serwer nie odpowiada.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:  
  
- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- IDCANCEL, jeśli użytkownik anulował okno dialogowe.  
  
- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj `COleDialog::GetLastError` funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIBusy](/windows/desktop/api/oledlg/nf-oledlg-oleuibusya) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_bz](#m_bz) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.  
  
##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType  
 Wywołaj tę funkcję można pobrać typu Wybór wybierany przez użytkownika w oknie dialogowym serwer jest zajęty.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ dokonano wyboru.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracanej są określane przez `Selection` typ wyliczeniowy zadeklarowany w `COleBusyDialog` klasy.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Wykonaj krótkie opisy tych wartości:  
  
- `COleBusyDialog::switchTo` Przełącz do przycisk został naciśnięty.  
  
- `COleBusyDialog::retry` Został naciśnięty przycisk Ponów próbę.  
  
- `COleBusyDialog::callUnblocked` Wywołanie, aby uaktywnić serwer jest teraz odblokowana.  
  
##  <a name="m_bz"></a>  COleBusyDialog::m_bz  
 Struktury typu OLEUIBUSY używane do sterowania zachowaniem serwer zajęty okno dialogowe.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Uwagi  
 Można modyfikować składowe tej struktury, bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
