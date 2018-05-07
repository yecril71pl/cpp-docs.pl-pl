---
title: Klasa CSettingsStoreSP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1852f4e280fa49a2436c421d4669e9d735d66c3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csettingsstoresp-class"></a>Klasa CSettingsStoreSP
`CSettingsStoreSP` Klasy to klasa pomocy, która służy do tworzenia wystąpień [CSettingsStore klasy](../../mfc/reference/csettingsstore-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Konstruuje `CSettingsStoreSP` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|Tworzy wystąpienie klasy, która jest pochodną `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Ustawia klasę środowiska uruchomieniowego. `Create` — Metoda używa klasy środowiska uruchomieniowego w celu określenia obiektów, aby utworzyć klasę.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`m_dwUserData`|Dane użytkownika są przechowywane w `CSettingsStoreSP` obiektu. Podaj dane w Konstruktorze `CSettingsStoreSP` obiektu.|  
|`m_pRegistry`|`CSettingsStore`-Pochodnych obiekt, który `Create` metoda tworzy.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `CSettingsStoreSP` klasę, aby przekierować wszystkie operacje rejestru MFC do innych lokalizacji, takich jak plik XML lub bazy danych. W tym celu wykonaj następujące czynności:  
  
1.  Utwórz klasę (takich jak `CMyStore`) i pochodzi ona z `CSettingsStore`.  
  
2.  Użyj [declare_dyncreate —](run-time-object-model-services.md#declare_dyncreate) i [implement_dyncreate —](run-time-object-model-services.md#implement_dyncreate) makra z niestandardowe `CSettingsStore` klasę, aby włączyć tworzenie dynamiczne.  
  
3.  Przesłonić funkcje wirtualne i wdrożenie `Read` i `Write` funkcji klasę niestandardową. Implementuje innych funkcji, do odczytywania i zapisywania danych do preferowanej lokalizacji.  
  
4.  W aplikacji, należy wywołać `CSettingsStoreSP::SetRuntimeClass` i przekaż we wskaźniku do [struktury CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) uzyskane z klasy.  
  
 Zawsze, gdy platformę zwykle może uzyskać dostępu do rejestru, go będzie teraz dynamicznie utworzyć wystąpienia klasy niestandardowej i używać go do odczytu lub zapisu danych.  
  
 `CSettingsStoreSP::SetRuntimeClass` wykorzystuje globalne zmienna statyczna. W związku z tym tylko jeden magazyn niestandardowy jest dostępna w czasie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsettingsstore.h  
  
##  <a name="create"></a>  CSettingsStoreSP::Create  
 Tworzy nowe wystąpienie obiektu, który jest pochodną [CSettingsStore klasy](../../mfc/reference/csettingsstore-class.md).  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bAdmin`  
 Parametr wartość logiczna określająca czy `CSettingsStore` obiekt jest tworzony w trybie administratora.  
  
 [in] `bReadOnly`  
 Parametr wartość logiczna określająca czy `CSettingsStore` obiekt jest tworzony na dostęp tylko do odczytu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do nowo utworzony `CSettingsStore` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć metody [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) Określanie typu obiektu `CSettingsStoreSP::Create` zostanie utworzona. Domyślnie ta metoda tworzy `CSettingsStore` obiektu.  
  
 W przypadku utworzenia `CSettingsStore` obiektów w trybie administratora, domyślna lokalizacja dla każdego dostępu z rejestru to HKEY_LOCAL_MACHINE. W przeciwnym razie wartość domyślną lokalizacją dla wszystkich dostępu do rejestru jest HKEY_CURRENT_USER.  
  
 Jeśli `bAdmin` jest `TRUE`, aplikacja musi mieć prawa administracyjne. W przeciwnym razie nie będzie, podczas próby dostępu do rejestru.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `Create` metody `CSettingsStoreSP` klasy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP  
 Konstruuje [klasy CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) obiektu.  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `dwUserData`  
 Dane zdefiniowane przez użytkownika który `CSettingsStoreSP` obiekt magazynów.  
  
### <a name="remarks"></a>Uwagi  
 `CSettingsStoreSP` Obiekt przechowuje dane z `dwUserData` w zmiennej członka chronionego `m_dwUserData`.  
  
##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass  
 Ustawia klasę środowiska uruchomieniowego. Metoda [CSettingsStoreSP::Create](#create) korzysta klasa środowiska uruchomieniowego, aby określić typ obiektu do utworzenia.  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pRTI`  
 Wskaźnik do informacji o klasie czasu wykonywania dla klasy pochodzące z [CSettingsStore klasy](../../mfc/reference/csettingsstore-class.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` w przypadku powodzenia; `FALSE` Jeśli klasa jest oznaczona `pRTI` nie pochodzi od `CSettingsStore`.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć [klasy CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) wyprowadzenia klasy z `CSettingsStore`. Użyj metody `SetRuntimeClass` Jeśli chcesz utworzyć obiektów klasy niestandardowej pochodzącej z `CSettingsStore`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md)
