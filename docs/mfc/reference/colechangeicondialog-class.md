---
title: Klasa COleChangeIconDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs: C++
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 237c1fcbea36c4e978ca19b14def4d57a4470973
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="colechangeicondialog-class"></a>Klasa COleChangeIconDialog
Używane dla okna dialogowego OLE Zmień ikonę.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Konstruuje `COleChangeIconDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Wykonuje określony w oknie dialogowym zmiany.|  
|[COleChangeIconDialog::DoModal](#domodal)|Wyświetla okno dialogowe OLE 2 Zmień ikonę.|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera dojścia do metaplik skojarzonych z formularzem ikony, tego elementu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, która steruje zachowaniem w oknie dialogowym.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleChangeIconDialog` umożliwia wywołanie tego okna dialogowego. Po `COleChangeIconDialog` obiekt został skonstruowany, możesz użyć [m_ci](#m_ci) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_ci` Struktura jest typu **OLEUICHANGEICON**. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktury w zestawie Windows SDK.  
  
 Aby uzyskać informacje o oknach dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog  
 Ta funkcja tworzy tylko `COleChangeIconDialog` obiektu.  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskazuje element do skonwertowania.  
  
 `dwFlags`  
 Tworzenie flagę zawiera dowolną liczbę następujące wartości łączyć, używając operatora testu koniunkcji- lub operator:  
  
- **CIF_SELECTCURRENT** Określa, że bieżący przycisk radiowy wybrany zostanie początkowo wywołanego okna dialogowego. Domyślnie włączone.  
  
- **CIF_SELECTDEFAULT** Określa, że przycisk radiowy domyślny wybrany zostanie początkowo wywołanego okna dialogowego.  
  
- **CIF_SELECTFROMFILE** Określa, że przycisk radiowy z pliku wybrany zostanie początkowo wywołanego okna dialogowego.  
  
- **CIF_SHOWHELP** Określa, czy przycisk Pomoc, aby będą wyświetlane, gdy jest wywoływana w oknie dialogowym.  
  
- **CIF_USEICONEXE** Określa, czy ikona powinny zostać wyodrębniony z plik wykonywalny określony w **szIconExe** pole [m_ci](#m_ci) zamiast pobranej z typu. Jest to przydatne do osadzania lub łączenia plików innych niż OLE.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne okna dialogowego zostanie ustawiona do okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktury w zestawie Windows SDK.  
  
##  <a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon  
 Wywołanie tej funkcji, aby zmienić ikony reprezentującej element do wybranego w oknie dialogowym po [DoModal](#domodal) zwraca **IDOK**.  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskazuje element, którego ikonę jest zmieniana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zmiany zakończy się pomyślnie; w przeciwnym razie 0.  
  
##  <a name="domodal"></a>COleChangeIconDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe OLE Zmień ikonę.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj `COleDialog::GetLastError` funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_ci](#m_ci) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, innego członka można wywołać funkcji, aby uzyskać ustawienia i informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.  
  
##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile  
 Wywołanie tej funkcji można uzyskać dojścia do Metaplik zawierający odpowiednikiem aspekt wybranego elementu.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do Metaplik zawierający odpowiednikiem aspekt ikonę Nowy, jeśli okno dialogowe zostało odrzucone przez wybranie **OK**; w przeciwnym razie ikona, ponieważ był przed został wyświetlony w oknie dialogowym.  
  
##  <a name="m_ci"></a>COleChangeIconDialog::m_ci  
 Struktura typu **OLEUICHANGEICON** służące do sterowania zachowaniem okno dialogowe Zmienianie ikony.  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
