---
title: Rejestrowanie formantów OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e51e4c425d3d16b57a2b1ce0d4fc2f585dc505d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378060"
---
# <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE
Formanty OLE, podobnie jak inne obiekty serwera OLE są dostępne przez inne aplikacje świadome OLE. Jest to osiągane przez rejestrowanie biblioteki typów i klasy formantu.  
  
 Następujące funkcje umożliwiają dodawanie i usuwanie formantu klasy strony właściwości i biblioteki typów w bazie danych rejestracji systemu Windows:  
  
### <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE  
  
|||  
|-|-|  
|[Afxoleregistercontrolclass —](#afxoleregistercontrolclass)|Dodaje klasę formantu w bazie danych rejestracji.|  
|[Afxoleregisterpropertypageclass —](#afxoleregisterpropertypageclass)|Dodaje strony właściwości formantu w bazie danych rejestracji.|  
|[Afxoleregistertypelib —](#afxoleregistertypelib)|Dodaje biblioteki typu formantu w bazie danych rejestracji.|  
|[Afxoleunregisterclass —](#afxoleunregisterclass)|Usuwa z bazy danych rejestracji klasy formantu lub klasy strony właściwości.|  
|[Afxoleunregistertypelib —](#afxoleunregistertypelib)|Usuwa biblioteki typu formantu z bazy danych rejestracji.|  
  
 `AfxOleRegisterTypeLib` Zazwyczaj jest wywoływana w celu wykonania Biblioteka DLL sterowania `DllRegisterServer`. Podobnie `AfxOleUnregisterTypeLib` jest wywoływana przez `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, i `AfxOleUnregisterClass` są zwykle nazywane `UpdateRegistry` funkcji członkowskiej klasy formantu strony fabryki lub właściwości.  
  
##  <a name="afxoleregistercontrolclass"></a>  Afxoleregistercontrolclass —  
 Rejestruje klasy formantu z bazy danych rejestracji systemu Windows.  
  
```   
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,  
    REFCLSID clsid,  
    LPCTSTR pszProgID,  
    UINT idTypeName,  
    UINT idBitmap,  
    int nRegFlags,  
    DWORD dwMiscStatus,  
    REFGUID tlid,  
    WORD wVerMajor,  
    WORD wVerMinor); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście wystąpienia modułu skojarzone z klasy formantu.  
  
 `clsid`  
 Identyfikator unikatowy klasy formantu.  
  
 `pszProgID`  
 Unikatowy identyfikator formantu.  
  
 `idTypeName`  
 Identyfikator zasobu ciągu zawierającego nazwę użytkownika do odczytu typu formantu.  
  
 *idBitmap*  
 Identyfikator zasobu mapy bitowej używany do reprezentowania formantu OLE w pasku narzędzi lub palety.  
  
 `nRegFlags`  
 Zawiera co najmniej jeden z następujących flag:  
  
- `afxRegInsertable` Zapewnia kontrolę pojawią się w oknie dialogowym Wstaw obiekt dla obiektów OLE.  
  
- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze ThreadingModel = apartamentu.  
  
- `afxRegFreeThreading` Ustawia model wątkowości w rejestrze ThreadingModel = wolne.  
  
     Możesz połączyć ze sobą dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` można ustawić ThreadingModel = jednocześnie. Zobacz [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) w zestawie SDK systemu Windows, aby uzyskać więcej informacji o rejestracji modelu wątkowości.  
  
> [!NOTE]
>  W wersjach MFC przed MFC 4.2 `int` `nRegFlags` parametru **BOOL** parametru *bInsertable*, którego dozwolone lub niedozwolone formantu ma zostać wstawiony w oknie dialogowym Wstaw obiekt pole.  
  
 *dwMiscStatus*  
 Zawiera co najmniej jeden z następujących flag stanu (opis flagi, zawiera **OLEMISC** wyliczenia w zestawie Windows SDK):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 Unikatowy identyfikator klasy formantu.  
  
 `wVerMajor`  
 Numer wersji głównej klasy formantu.  
  
 `wVerMinor`  
 Numer wersji pomocniczej klasy formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli klasa formant został zarejestrowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia to kontrolę mają być używane przez kontenery, które są OLE-control. `AfxOleRegisterControlClass` aktualizuje rejestr przy użyciu nazwy i lokalizacji w systemie kontroli, a także ustawia model wątkowy obsługującego formantu w rejestrze. Aby uzyskać więcej informacji, zobacz [64 Uwaga techniczna](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Komórkowy Model wątkowości w OLE formantów," i [o procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms681917) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 W powyższym przykładzie pokazano, jak `AfxOleRegisterControlClass` jest wywoływana z flagą dla insertable i Flaga apartamentu modelu operacja logiczna ze sobą w celu utworzenia szóstego parametru:  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 Formant będą widoczne w oknie dialogowym Wstaw obiekt włączone kontenery i będzie obsługujący modelu typu apartment. Formanty obsługujący modelu typu apartment musi zapewnić tej klasy statyczne, które dane są chronione przez blokad, tak, aby podczas kontroli w jednym apartamentu uzyskuje dostęp do danych statycznych, nie jest wyłączone przez harmonogram przed zakończeniem, a inne wystąpienie tego samego rodzaju, który rozpoczyna się przy użyciu te same dane statyczne. Sekcja krytyczna kodu jest otoczony żadnych operacji uzyskania dostępu do danych statycznych.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>  Afxoleregisterpropertypageclass —  
 Rejestruje klasy strony właściwości z bazy danych rejestracji systemu Windows.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście wystąpienia modułu skojarzone z klasy strony właściwości.  
  
 `clsid`  
 Identyfikator unikatowy klasy strony właściwości.  
  
 `idTypeName`  
 Identyfikator zasobu ciągu zawierającego nazwę użytkownika do odczytu strony właściwości.  
  
 `nRegFlags`  
 Może zawierać flagi:  
  
- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze ThreadingModel = apartamentu.  
  
> [!NOTE]
>  W wersjach MFC przed MFC 4.2 `int` `nRegFlags` parametru nie jest dostępna. Należy zauważyć, że `afxRegInsertable` flaga nie jest prawidłową opcją dla strony właściwości i spowoduje ASSERT w MFC jest ustawiona  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli klasa formant został zarejestrowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu strony właściwości, które mają być używane przez kontenery, które są OLE-control. `AfxOleRegisterPropertyPageClass` zaktualizowanie rejestru o nazwie strony właściwości i jego lokalizacji w systemie, a także ustawia model wątkowy obsługującego formantu w rejestrze. Aby uzyskać więcej informacji, zobacz [64 Uwaga techniczna](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Komórkowy Model wątkowości w OLE formantów," i [o procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms681917) w zestawie Windows SDK.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>  Afxoleregistertypelib —  
 Rejestruje biblioteki typów z bazy danych rejestracji systemu Windows i umożliwia biblioteki typów, które mają być używane przez inne kontenerów, które są OLE-control.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście wystąpienia aplikacji skojarzonej z biblioteki typów.  
  
 *tlid*  
 Unikatowy identyfikator biblioteki typów.  
  
 *pszFileName*  
 Wskazuje opcjonalna nazwa pliku biblioteki typów zlokalizowanych (. Plik biblioteki TLB) dla formantu.  
  
 *pszHelpDir*  
 Nazwa katalogu, w którym można znaleźć w pliku pomocy biblioteki typów. Jeśli **NULL**, plik pomocy zakłada, że w tym samym katalogu co samej biblioteki typów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli biblioteka typów została zarejestrowana; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja aktualizuje rejestr przy nazwy biblioteki typów i jego lokalizacji w systemie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>  Afxoleunregisterclass —  
 Usuwa wpis klasy strony formantu lub właściwości z bazy danych rejestracji systemu Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator clsID*  
 Identyfikator unikatowy klasy strony formantu lub właściwości.  
  
 `pszProgID`  
 Unikatowy identyfikator formantu lub właściwości strony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant lub właściwość klasy strony został pomyślnie wyrejestrowany; w przeciwnym razie 0.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>  Afxoleunregistertypelib —  
 Wywołanie tej funkcji, aby usunąć wpis biblioteki typu z bazy danych rejestracji systemu Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Parametry  
 `tlID`  
 Unikatowy identyfikator biblioteki typów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli biblioteka typów została pomyślnie wyrejestrowano; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
