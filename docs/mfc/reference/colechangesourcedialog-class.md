---
title: Klasa COleChangeSourceDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
dev_langs:
- C++
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08b4095b535724f7132a2b286ce52cb46286932b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037599"
---
# <a name="colechangesourcedialog-class"></a>Klasa COleChangeSourceDialog
Używane dla okna dialogowego OLE Zmienianie źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Konstruuje `COleChangeSourceDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeSourceDialog::DoModal](#domodal)|Wyświetla okno dialogowe OLE Zmienianie źródła.|  
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Pobiera nazwę wyświetlaną pełną źródła.|  
|[COleChangeSourceDialog::GetFileName](#getfilename)|Pobiera nazwę pliku z nazwą źródłowego.|  
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Pobiera prefiks poprzedniej źródła.|  
|[COleChangeSourceDialog::GetItemName](#getitemname)|Pobiera nazwę elementu z nazwą źródłowego.|  
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Pobiera prefiks nowego źródła|  
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Wskazuje, czy źródło jest nieprawidłowy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, która steruje zachowaniem w oknie dialogowym.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleChangeSourceDialog` umożliwia wywołanie tego okna dialogowego. Po `COleChangeSourceDialog` obiekt został skonstruowany, możesz użyć [m_cs](#m_cs) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_cs` Struktura jest typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160). Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
 Aby uzyskać informacje o oknach dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog  
 Ta funkcja tworzy `COleChangeSourceDialog` obiektu.  
  
```  
explicit COleChangeSourceDialog(
    COleClientItem* pItem,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Wskaźnik do połączonego [COleClientItem](../../mfc/reference/coleclientitem-class.md) źródłem ma zostać zaktualizowany.  
  
 *pParentWnd*  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne okna dialogowego zostanie ustawiona do okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury i [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkcji w zestawie Windows SDK.  
  
##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe OLE Zmienianie źródła.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_cs](#m_cs) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, można wywołać elementu członkowskiego funkcji można pobrać ustawień wprowadzonych przez użytkownika lub informacji z okna dialogowego. Poniższa lista zawiera nazwy zapytania typowe funkcje:  
  
- [GetFileName](#getfilename)  
  
- [GetDisplayName](#getdisplayname)  
  
- [GetItemName](#getitemname)  
  
##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName  
 Wywołanie tej funkcji można pobrać Pełna nazwa wyświetlana dla elementu połączonych klientów.  
  
```  
CString GetDisplayName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Źródło pełną nazwę wyświetlaną (moniker) [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonym w konstruktorze.  
  
##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName  
 Wywołanie tej funkcji można pobrać części krótkiej nazwy pliku nazwę wyświetlaną dla elementu połączonych klientów.  
  
```  
CString GetFileName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Część krótkiej nazwy pliku nazwa wyświetlana źródła [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonym w konstruktorze.  
  
### <a name="remarks"></a>Uwagi  
 Krótka nazwa pliku wraz z krótkiej nazwy elementu daje Pełna nazwa wyświetlana.  
  
##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix  
 Wywołanie tej funkcji można pobrać poprzedni ciąg prefiksu dla tego źródła.  
  
```  
CString GetFromPrefix();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg prefiksu poprzedniej źródła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
 Ta wartość pochodzi bezpośrednio z **lpszFrom** członkiem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName  
 Wywołanie tej funkcji można pobrać części krótkiej nazwy elementu nazwę wyświetlaną dla elementu połączonych klientów.  
  
```  
CString GetItemName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Część krótkiej nazwy elementu źródłowego nazwę wyświetlaną [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonym w konstruktorze.  
  
### <a name="remarks"></a>Uwagi  
 Krótka nazwa pliku wraz z krótkiej nazwy elementu daje Pełna nazwa wyświetlana.  
  
##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix  
 Wywołanie tej funkcji, aby uzyskać nowy ciąg prefiksu dla tego źródła.  
  
```  
CString GetToPrefix();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg prefiksu nowego źródła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
 Ta wartość pochodzi bezpośrednio z **lpszTo** członkiem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs  
 Ten element członkowski danych to struktura typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160).  
  
```  
OLEUICHANGESOURCE m_cs;  
```  
  
### <a name="remarks"></a>Uwagi  
 `OLEUICHANGESOURCE` Służy do sterowania zachowaniem okno dialogowe OLE Zmienianie źródła. Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource  
 Wywołanie tej funkcji w celu ustalenia, czy nowe źródło jest prawidłowy.  
  
```  
BOOL IsValidSource();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli nowe źródło jest prawidłowa, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
