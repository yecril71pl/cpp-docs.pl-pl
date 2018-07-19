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
ms.openlocfilehash: ea2c87a3ce87bbf15f99609a643a9a72f6d2058e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853488"
---
# <a name="colechangesourcedialog-class"></a>Klasa COleChangeSourceDialog
Stosowane dla okna dialogowego OLE Zmień źródło.  
  
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
|[COleChangeSourceDialog::DoModal](#domodal)|Wyświetla okna dialogowego OLE Zmień źródło.|  
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Pobiera nazwę wyświetlaną pełną źródła.|  
|[COleChangeSourceDialog::GetFileName](#getfilename)|Pobiera nazwę pliku na podstawie nazwy źródła.|  
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Pobiera prefiks poprzedniego źródła.|  
|[COleChangeSourceDialog::GetItemName](#getitemname)|Pobiera nazwę elementu z nazwę źródła.|  
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Pobiera prefiks nowe źródło|  
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Wskazuje, czy źródło jest prawidłowy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, która steruje zachowaniem okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleChangeSourceDialog` umożliwia wywołanie tego okna dialogowego. Po `COleChangeSourceDialog` obiekt został skonstruowany, możesz użyć [m_cs](#m_cs) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_cs` Struktury jest typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160). Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcja elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji o okna dialogowe OLE specyficzne artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
 Wskaźnik do połączoną [COleClientItem](../../mfc/reference/coleclientitem-class.md) źródła, którego ma zostać zaktualizowany.  
  
 *pParentWnd*  
 Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe zostanie ustawiona do okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury i [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkcji w zestawie Windows SDK.  
  
##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal  
 Wywołaj tę funkcję, aby wyświetlić okna dialogowego OLE Zmień źródło.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:  
  
- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- IDCANCEL, jeśli użytkownik anulował okno dialogowe.  
  
- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_cs](#m_cs) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca IDOK, można wywołać element członkowski funkcji można pobrać ustawień wprowadzonych przez użytkownika lub informacji z okna dialogowego. Poniższa lista zawiera nazwy funkcje typowych zapytań:  
  
- [GetFileName](#getfilename)  
  
- [GetDisplayName](#getdisplayname)  
  
- [GetItemName](#getitemname)  
  
##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName  
 Wywołaj tę funkcję, aby pobrać Pełna nazwa wyświetlana elementu połączonych klientów.  
  
```  
CString GetDisplayName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Źródło pełną nazwę wyświetlaną (monikera) [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.  
  
##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName  
 Wywołaj tę funkcję, aby pobrać część krótkiej nazwy pliku nazwę wyświetlaną dla elementu połączonych klientów.  
  
```  
CString GetFileName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Część krótkiej nazwy pliku nazwa wyświetlana źródła [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.  
  
### <a name="remarks"></a>Uwagi  
 Moniker plików wraz z moniker elementu zapewnia Pełna nazwa wyświetlana.  
  
##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix  
 Wywołaj tę funkcję można pobrać poprzednich Ciąg prefiksu dla źródła.  
  
```  
CString GetFromPrefix();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg prefiksu poprzedniego źródła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji dopiero po [DoModal](#domodal) zwraca IDOK.  
  
 Ta wartość pochodzi bezpośrednio z `lpszFrom` członkiem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName  
 Wywołaj tę funkcję, aby pobrać część moniker elementu nazwę wyświetlaną dla elementu połączonych klientów.  
  
```  
CString GetItemName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Część moniker elementu nazwę wyświetlaną źródła [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.  
  
### <a name="remarks"></a>Uwagi  
 Moniker plików wraz z moniker elementu zapewnia Pełna nazwa wyświetlana.  
  
##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix  
 Wywołaj tę funkcję, aby uzyskać nowy ciąg prefiksu dla źródła.  
  
```  
CString GetToPrefix();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg prefiksu nowego źródła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji dopiero po [DoModal](#domodal) zwraca IDOK.  
  
 Ta wartość pochodzi bezpośrednio z `lpszTo` członkiem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs  
 Ten element członkowski danych to strukturę typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160).  
  
```  
OLEUICHANGESOURCE m_cs;  
```  
  
### <a name="remarks"></a>Uwagi  
 `OLEUICHANGESOURCE` Służy do sterowania zachowaniem okna dialogowego OLE Zmień źródło. Można bezpośrednio modyfikować składowe tej struktury.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource  
 Wywołaj tę funkcję, aby ustalić, czy nowe źródło jest prawidłowy.  
  
```  
BOOL IsValidSource();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli nowe źródło jest prawidłowa, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji dopiero po [DoModal](#domodal) zwraca IDOK.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
