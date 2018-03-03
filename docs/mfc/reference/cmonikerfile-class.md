---
title: Klasa CMonikerFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3dfdf86a4375521d7db084b60c549b08a54dc992
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmonikerfile-class"></a>Klasa CMonikerFile
Reprezentuje strumienia danych ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) o nazwie [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Konstruuje `CMonikerFile` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|Odłącza i zwalnia strumienia i zwalnia krótkiej nazwy.|  
|[CMonikerFile::Detach](#detach)|Odłącza `IMoniker` tego `CMonikerFile` obiektu.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Zwraca bieżący krótkiej nazwy.|  
|[CMonikerFile::Open](#open)|Otwiera określony plik można uzyskać strumienia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Pobiera kontekst powiązania lub tworzy domyślnie zainicjowane, kontekst powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Krótka nazwa zawiera informacje, podobnie jak ścieżka do pliku. Jeśli masz wskaźnik do obiektu moniker `IMoniker` interfejsu, może uzyskać dostęp do określonych plików bez potrzeby innych szczegółowych informacji o którym rzeczywiście znajduje się plik.  
  
 Pochodną `COleStreamFile`, `CMonikerFile` przyjmuje krótka nazwa lub reprezentację ciągu go do krótkiej nazwy i wiąże strumienia, dla której krótka nazwa jest nazwą. Następnie można odczytać i zapisać w strumieniu. Rzeczywistego celu `CMonikerFile` jest zapewnienie dostępu `IStream`o nazwie s `IMoniker`s, dzięki czemu nie trzeba powiązać strumienia samodzielnie, jeszcze `CFile` funkcji do strumienia.  
  
 `CMonikerFile`Nie można powiązać z innym niż strumienia. Jeśli chcesz powiązać z magazynu lub obiekt, należy użyć `IMoniker` interfejsu bezpośrednio.  
  
 Aby uzyskać więcej informacji o strumieni i monikerów, zobacz [COleStreamFile](../../mfc/reference/colestreamfile-class.md) w *odwołania MFC* i [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) i [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705) w Zestaw Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="close"></a>CMonikerFile::Close  
 Wywołanie tej funkcji, odłącz i wersji strumienia i zwolnić krótkiej nazwy.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać dla strumieni nieotwarte lub już zamknięty.  
  
##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile  
 Konstruuje `CMonikerFile` obiektu.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext  
 Wywołanie tej funkcji można utworzyć kontekstu wiązania domyślnie zainicjowane.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Parametry  
 `pError`  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona do przyczyna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do kontekstu powiązania [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) powiązania z w przypadku powodzenia; w przeciwnym razie **NULL**. Jeśli wystąpienie została otwarta z `IBindHost` interfejsu, kontekst powiązania są pobierane z `IBindHost`. W przypadku nie `IBindHost` interfejsu lub interfejsu nie może zwracać kontekstu powiązania, tworzenia kontekstu powiązania. Opis [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) interfejsu, zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Kontekst powiązania jest obiekt, który przechowuje informacje dotyczące operacji wiązania określonego krótkiej nazwy. Można zastąpić tę funkcję, aby zapewnić kontekstu wiązania niestandardowego.  
  
##  <a name="detach"></a>CMonikerFile::Detach  
 Wywołanie tej funkcji, aby zamknąć strumienia.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pError`  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona do przyczyna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="getmoniker"></a>CMonikerFile::GetMoniker  
 Wywołanie tej funkcji można pobrać wskaźnik do bieżącego krótkiej nazwy.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego interfejsu moniker ( [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CMonikerFile` nie jest interfejsem, zwrócony wskaźnik nie zwiększa się liczba odwołań (za pośrednictwem [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)), i krótka nazwa zostanie zwolniony podczas `CMonikerFile` obiektu zostanie zwolniony. Jeśli chcesz przechowywać na moniker lub zwolnij samodzielnie, należy najpierw `AddRef` go.  
  
##  <a name="open"></a>CMonikerFile::Open  
 Wywołanie tej funkcji członkowskich można otworzyć obiektu pliku lub krótkiej nazwy.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszURL`  
 Adres URL lub nazwa pliku, który ma zostać otwarty.  
  
 `pError`  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona do przyczyna.  
  
 `pMoniker`  
 Wskaźnik do interfejsu moniker `IMoniker` ma być używany do uzyskania strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `lpszURL` Parametru nie można używać na komputerze Macintosh. Tylko `pMoniker` formę **Otwórz** może być używany na komputerze Macintosh.  
  
 Możesz użyć adresu URL lub nazwę pliku dla `lpszURL` parametru. Na przykład:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - lub -  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleStreamFile](../../mfc/reference/colestreamfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
