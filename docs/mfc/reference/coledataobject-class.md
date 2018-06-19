---
title: Klasa COleDataObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9cd159597440dfb55bbe8abe147623096cdf449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374513"
---
# <a name="coledataobject-class"></a>Klasa COleDataObject
Używany podczas transferów danych do odzyskiwania danych w różnych formatach ze Schowka, za pomocą operacji przeciągania i upuszczania, lub z elementu osadzone OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|Konstruuje `COleDataObject` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|Dołącza określony obiekt danych OLE do `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Dołącza obiektu danych w Schowku.|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Przygotowuje dla jednego lub więcej kolejnych `GetNextFormat` wywołania.|  
|[COleDataObject::Detach](#detach)|Odłącza skojarzony `IDataObject` obiektu.|  
|[COleDataObject::GetData](#getdata)|Kopiuje dane z przyłączonego obiektu danych OLE w określonym formacie.|  
|[COleDataObject::GetFileData](#getfiledata)|Kopiuje dane z przyłączonego obiektu danych OLE w `CFile` wskaźnika w określonym formacie.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopiuje dane z przyłączonego obiektu danych OLE w `HGLOBAL` w określonym formacie.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Zwraca następny dostępny format danych.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Sprawdza, czy dane są dostępne w określonym formacie.|  
|[COleDataObject::Release](#release)|Odłącza i zwalnia skojarzony `IDataObject` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDataObject` nie ma klasy podstawowej.  
  
 Tego rodzaju transferów danych obejmują źródło i lokalizację docelową. Źródło danych jest zaimplementowany jako obiekt [COleDataSource](../../mfc/reference/coledatasource-class.md) klasy. Zawsze, gdy został porzucony w nim danych lub jest monit o wykonanie operacji wklejania ze Schowka obiektu w aplikacji docelowej `COleDataObject` można utworzyć klasy.  
  
 Ta klasa umożliwia określenie, czy dane istnieje w określonym formacie. Można także wyliczyć formatów dostępnych danych lub sprawdź, czy dany format jest dostępna i następnie pobrać dane w formacie preferowany. Pobieranie obiektu można wykonywać na kilka różnych sposobów, łącznie z użyciem [cfile —](../../mfc/reference/cfile-class.md), `HGLOBAL`, lub **STGMEDIUM** struktury.  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji o używaniu obiektów danych w aplikacji, zobacz artykuł [obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `COleDataObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="attach"></a>  COleDataObject::Attach  
 Wywołanie tej funkcji, aby skojarzyć `COleDataObject` obiektu z obiektu danych.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDataObject*  
 Wskazuje obiektu danych.  
  
 `bAutoRelease`  
 **Wartość TRUE,** będą obiekcie danych OLE zwalniana, kiedy `COleDataObject` obiekt jest niszczone; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) w zestawie Windows SDK.  
  
##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard  
 Wywołanie tej funkcji, aby dołączyć obiekt danych, który jest aktualnie w Schowku do `COleDataObject` obiektu.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Wywołanie tej funkcji powoduje zablokowanie Schowka do czasu zwolnienia jest ten obiekt danych. Obiekt danych jest opublikowane w destruktor dla elementu `COleDataObject`. Aby uzyskać więcej informacji, zobacz [Funkcja OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048) i [Funkcja CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) w dokumentacji systemu Win32.  
  
##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats  
 Wywołanie tej funkcji, aby przygotować się do kolejnych wywołań `GetNextFormat` do pobierania listy formatów danych z elementu.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu `BeginEnumFormats`, znajduje się pozycja format pierwszej obsługiwana przez ten obiekt danych. Kolejne wywołania `GetNextFormat` wylicza listę dostępnych formatów w obiekcie danych.  
  
 Aby sprawdzić dostępność danych w danym formacie, użyj [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Aby uzyskać więcej informacji, zobacz [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) w zestawie Windows SDK.  
  
##  <a name="coledataobject"></a>  COleDataObject::COleDataObject  
 Konstruuje `COleDataObject` obiektu.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [COleDataObject::Attach](#attach) lub [COleDataObject::AttachClipboard](#attachclipboard) musi być dokonana przed wywołaniem innych `COleDataObject` funkcji.  
  
> [!NOTE]
>  Ponieważ jeden z parametrów do obsługi przeciągania i upuszczania jest wskaźnik do `COleDataObject`, nie istnieje potrzeba do wywołania tego konstruktora do obsługi przeciągania i upuszczania.  
  
##  <a name="detach"></a>  COleDataObject::Detach  
 Wywołanie tej funkcji można odłączyć `COleDataObject` obiekt z jego skojarzony obiekt danych OLE bez zwolnienia obiektu danych.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu danych OLE, która została odłączona.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getdata"></a>  COleDataObject::GetData  
 Wywołanie tej funkcji do pobierania danych z elementu w określonym formacie.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format, w którym ma zostać zwrócone dane. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpStgMedium`  
 Wskazuje [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) strukturę, która będzie odbierać dane.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, wartości domyślne są używane w przypadku innych pól w **FORMATETC** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="getfiledata"></a>  COleDataObject::GetFileData  
 Wywołanie tej funkcji, aby utworzyć `CFile` lub `CFile`-pochodnych obiektu oraz do pobierania danych w określonym formacie do `CFile` wskaźnika.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format, w którym ma zostać zwrócone dane. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, wartości domyślne są używane w przypadku innych pól w **FORMATETC** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego `CFile` lub `CFile`-pochodnej obiektu zawierającego dane w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 W zależności od średniej, dane są przechowywane w, może być typu rzeczywistego wskazywanej przez wartość zwracaną `CFile`, `CSharedFile`, lub `COleStreamFile`.  
  
> [!NOTE]
>  `CFile` Właścicielem obiektu, dostęp do tej funkcji wartość zwracaną przez obiekt wywołujący. Jest odpowiedzialny za obiekt wywołujący, aby **usunąć** `CFile` obiektu, w tym samym zamykania pliku.  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData  
 Wywołanie tej funkcji można przydzielić pamięci globalnej bloku oraz do pobierania danych w określonym formacie do `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format, w którym ma zostać zwrócone dane. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, wartości domyślne są używane w przypadku innych pól w **FORMATETC** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście bloku pamięci globalnej zawierające dane w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat  
 Wywołanie tej funkcji, aby uzyskać formaty dostępne do pobrania danych z elementu.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) strukturę, która otrzymuje informacji o formacie po powrocie z wywołania funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest dostępna; innego formatu w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu [COleDataObject::BeginEnumFormats](#beginenumformats), znajduje się pozycja format pierwszej obsługiwana przez ten obiekt danych. Kolejne wywołania `GetNextFormat` wylicza listę dostępnych formatów w obiekcie danych. Użyj tych funkcji, aby wyświetlić listę dostępnych formatów.  
  
 Aby sprawdzić dostępność danego formatu, należy wywołać [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Aby uzyskać więcej informacji, zobacz [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) w zestawie Windows SDK.  
  
##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable  
 Wywołanie tej funkcji w celu ustalenia, czy określony format jest dostępna do pobrania danych z elementu OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formatu danych schowka do użycia w strukturze wskazywana przez `lpFormatEtc`. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujący żądany format. Podaj wartość dla tego parametru, tylko, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, wartości domyślne są używane w przypadku innych pól w **FORMATETC** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dane są dostępne w określonym formacie. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna przed wywołaniem `GetData`, `GetFileData`, lub `GetGlobalData`.  
  
 Aby uzyskać więcej informacji, zobacz [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>  COleDataObject::Release  
 Wywołanie tej funkcji, aby zwolnić własność [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) obiekt, który został wcześniej skojarzony z `COleDataObject` obiektu.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Uwagi  
 `IDataObject` Został skojarzony z `COleDataObject` przez wywołanie metody **Attach** lub `AttachClipboard` jawnie ani przez platformę. Jeśli `bAutoRelease` parametr **Attach** jest **FALSE**, `IDataObject` obiektu nie zostanie zwolniony. W takim przypadku obiekt wywołujący jest odpowiedzialny za zwolnienie `IDataObject` przez wywołanie metody [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [COleDataSource — klasa](../../mfc/reference/coledatasource-class.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
