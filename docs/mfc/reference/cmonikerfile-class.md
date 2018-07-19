---
title: Klasa CMonikerFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 296e288f017373563b867b02ad26f25ec6bc6227
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853650"
---
# <a name="cmonikerfile-class"></a>Klasa CMonikerFile
Przedstawia strumień danych ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) o nazwie określonej przez [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
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
|[CMonikerFile::Close](#close)|Powoduje odłączenie i zwalnia strumienia, a następnie zwalnia moniker.|  
|[CMonikerFile::Detach](#detach)|Odłącza `IMoniker` z tego `CMonikerFile` obiektu.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Zwraca bieżący krótkiej nazwy.|  
|[CMonikerFile::Open](#open)|Otwiera określony plik, aby uzyskać strumienia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Pobiera kontekst powiązania lub tworzy domyślnie zainicjowane, kontekst powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Krótka nazwa zawiera informacje, podobnie jak w nazwie ścieżki do pliku. Jeśli masz wskaźnik do obiektu moniker `IMoniker` interfejsu, mogą uzyskać dostęp do wskazany plik bez innych szczegółowych informacji o których faktycznie znajduje się plik.  
  
 Pochodną `COleStreamFile`, `CMonikerFile` krótka lub ciąg reprezentujący może sprawić, że do krótka i wiąże strumień, dla którego przydomek jest nazwą. Można następnie odczytu i zapisu do tego strumienia. Rzeczywistego celu `CMonikerFile` ma na celu dostarczenie prosty dostęp do `IStream`s o nazwie określonej przez `IMoniker`s tak, że nie masz można powiązać strumienia samodzielnie, jeszcze `CFile` funkcjonalność do strumienia.  
  
 `CMonikerFile` Nie można powiązać z coś innego niż strumienia. Jeśli chcesz powiązać z magazynu lub obiektu, należy użyć `IMoniker` interfejs bezpośrednio.  
  
 Aby uzyskać więcej informacji na temat strumieni i monikerów, zobacz [COleStreamFile](../../mfc/reference/colestreamfile-class.md) w *odwołanie MFC* i [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) i [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705) w Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="close"></a>  CMonikerFile::Close  
 Wywołaj tę funkcję do odłączenia i wersji strumienia i zwolnić moniker.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać dla strumieni nieotwarte lub już zamknięte.  
  
##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile  
 Konstruuje `CMonikerFile` obiektu.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext  
 Wywołaj tę funkcję, aby utworzyć domyślnie zainicjowane, kontekstu powiązania.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona przyczynie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do kontekstu powiązania [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) do powiązania z, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL. Jeśli wystąpienie zostało otwarte z `IBindHost` interfejsu, kontekst powiązania jest pobierana z `IBindHost`. Jeśli ma nie `IBindHost` interfejsu lub interfejs nie zwraca kontekst powiązania, tworzenia kontekstu powiązania. Aby uzyskać opis [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) interfejsu, zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Kontekst powiązania jest obiektem, który przechowuje informacje o operacji wiązania określonej krótkiej nazwy. Można zastąpić tę funkcję, aby zapewnić kontekst niestandardowego powiązania.  
  
##  <a name="detach"></a>  CMonikerFile::Detach  
 Wywołaj tę funkcję, aby zamknąć strumień.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona przyczynie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker  
 Wywołaj tę funkcję, aby pobrać wskaźnika do bieżącego krótkiej nazwy.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego interfejsu krótkiej nazwy ( [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CMonikerFile` nie jest interfejsem, zwrócony wskaźnik nie zwiększa liczbę odwołań (za pośrednictwem [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)), i moniker jest zwalniany podczas `CMonikerFile` obiektu jest zwalniany. Jeśli chcesz przechowywać na monikera lub wersji samodzielnie, musisz najpierw `AddRef` go.  
  
##  <a name="open"></a>  CMonikerFile::Open  
 Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik lub krótkiej nazwy obiektu.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszURL*  
 Adres URL lub nazwę pliku, który ma zostać otwarty.  
  
 *pError*  
 Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona przyczynie.  
  
 *pMoniker*  
 Wskaźnik do interfejsu moniker `IMoniker` ma być używany do uzyskania strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 *LpszURL* parametru nie można używać na komputerze Macintosh. Tylko *pMoniker* formy `Open` może być używany na komputerze Macintosh.  
  
 Możesz użyć adresu URL lub nazwę pliku do *lpszURL* parametru. Na przykład:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - lub —  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleStreamFile](../../mfc/reference/colestreamfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
