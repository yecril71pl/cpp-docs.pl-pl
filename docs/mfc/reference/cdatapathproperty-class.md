---
title: Klasa CDataPathProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2559b4917f16bb8ddc49b73ace8bda6e1a9bafc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367311"
---
# <a name="cdatapathproperty-class"></a>Klasa CDataPathProperty
Implementuje OLE kontrolować właściwości, które mogą być uruchamiane asynchronicznie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Konstruuje `CDataPathProperty` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Pobiera asynchroniczny formantu OLE skojarzony z `CDataPathProperty` obiektu.|  
|[CDataPathProperty::GetPath](#getpath)|Pobiera nazwę ścieżki właściwości.|  
|[CDataPathProperty::Open](#open)|Inicjuje Ładowanie asynchroniczne właściwości skojarzonym formancie ActiveX (OLE).|  
|[CDataPathProperty::ResetData](#resetdata)|Wywołania `CAsyncMonikerFile::OnDataAvailable` powiadomiono kontenera, w którym właściwości zostały zmienione.|  
|[CDataPathProperty::SetControl](#setcontrol)|Ustawia asynchronicznej formantu ActiveX (OLE) skojarzony z właściwością.|  
|[CDataPathProperty::SetPath](#setpath)|Ustawia nazwę ścieżki właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Załadowano asynchroniczne właściwości po rozpoczęciu synchronicznego.  
  
 Klasa `CDataPathProperty` jest pochodną **CAysncMonikerFile**. Aby zaimplementować właściwości asynchronicznego w formantów OLE, klasa wyprowadzona z `CDataPathProperty`i Zastąp [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Aby uzyskać więcej informacji o sposobie używania monikery asynchroniczne i formantów w aplikacji internetowych zobacz następujące artykuły:  
  
- [Internet pierwszych kroków: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet pierwszych kroków: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 Konstruuje `CDataPathProperty` obiektu.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Wskaźnik do obiektu OLE formantu ma zostać skojarzony z tym `CDataPathProperty` obiektu.  
  
 `lpszPath`  
 Ścieżki, która może być bezwzględny lub względny, używany do tworzenia asynchroniczne krótkiej nazwy odwołujących się do rzeczywistej lokalizacji bezwzględnej właściwości. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektów do pliku, dołączenie wartości `file://` do ścieżki.  
  
### <a name="remarks"></a>Uwagi  
 `COleControl` Obiekt wskazywany przez `pControl` jest używany przez **Otwórz** i pobrać klas pochodnych. Jeśli `pControl` jest **NULL**, kontrolki używane z **Otwórz** powinien być ustawiony z `SetControl`. Jeśli `lpszPath` jest **NULL**, można przekazać w ścieżce za pośrednictwem **Otwórz** lub ustaw ją z `SetPath`.  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 Wywołanie tej funkcji Członkowskich pobrać `COleControl` obiekt skojarzony z `CDataPathProperty` obiektu.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do formantu OLE skojarzone z `CDataPathProperty` obiektu. **Wartość NULL** Jeśli formant nie jest skojarzony.  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 Wywołanie tej funkcji Członkowskich, aby pobrać ścieżki, należy ustawić podczas `CDataPathProperty` obiekt został skonstruowany lub określone **Otwórz**, lub został określony w poprzednie wywołanie `SetPath` funkcję elementu członkowskiego.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę ścieżki do samej właściwości. Może być pusta, jeśli żadna ścieżka nie została określona.  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 Wywołanie tej funkcji Członkowskich zainicjować ładowania właściwości asynchronicznej formantu skojarzony.  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Wskaźnik do obiektu OLE formantu ma zostać skojarzony z tym `CDataPathProperty` obiektu.  
  
 `pError`  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona do przyczynę.  
  
 `lpszPath`  
 Ścieżki, która może być bezwzględny lub względny, używany do tworzenia asynchroniczne krótkiej nazwy odwołujących się do rzeczywistej lokalizacji bezwzględnej właściwości. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektów do pliku, dołączenie wartości `file://` do ścieżki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja próbuje uzyskać `IBindHost` interfejsu z formantu.  
  
 Przed wywołaniem **Otwórz** bez ścieżki, należy ustawić wartość dla właściwości ścieżki. Można to zrobić, gdy obiekt jest zbudowane, lub przez wywołanie metody `SetPath` funkcję elementu członkowskiego.  
  
 Przed wywołaniem **Otwórz** bez kontroli formantu ActiveX (wcześniej znane jako formant OLE) może być skojarzony z obiektem. Można to zrobić, gdy obiekt jest zbudowane, lub przez wywołanie metody `SetControl`.  
  
 Skompilowanie wszystkich przeciążeń [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) są także dostępne w `CDataPathProperty`.  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 Wywołanie tej funkcji, aby uzyskać `CAsyncMonikerFile::OnDataAvailable` powiadomiono kontenera zmieniono właściwości formantu, czy wszystkie informacje ładowany asynchronicznie nie jest już przydatne.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Uwagi  
 Otwieranie powinien zostać uruchomiony ponownie. Klasy pochodne mogą przesłaniać tę funkcję dla różnych ustawień domyślnych.  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć asynchroniczne kontrolkę OLE z `CDataPathProperty` obiektu.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Wskaźnik do asynchronicznego kontrolkę OLE ma być skojarzona z właściwością.  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 Wywołanie tej funkcji członkowskich można ustawić nazwy właściwości ścieżki.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPath`  
 Ścieżka, która może być bezwzględny lub względny właściwości ładowany asynchronicznie. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektów do pliku, dołączenie wartości `file://` do ścieżki.  
  
## <a name="see-also"></a>Zobacz też  
 [Obraz przykładowej MFC](../../visual-cpp-samples.md)   
 [Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
