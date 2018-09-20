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
ms.openlocfilehash: c2b80ab73c41d455b0715f15034b54197672b95d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424875"
---
# <a name="csettingsstoresp-class"></a>Klasa CSettingsStoreSP

`CSettingsStoreSP` Klasa to klasa pomocnika, która służy do tworzenia wystąpień [klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md).

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
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Ustawia klasy środowiska uruchomieniowego. `Create` Metoda używa klasy środowiska uruchomieniowego, aby określić klasę obiektów, które należy utworzyć.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_dwUserData`|Danych niestandardowych użytkownika, która jest przechowywana w `CSettingsStoreSP` obiektu. Należy podać te dane w Konstruktorze typu `CSettingsStoreSP` obiektu.|
|`m_pRegistry`|`CSettingsStore`-Pochodzi obiekt `Create` metoda tworzy.|

## <a name="remarks"></a>Uwagi

Możesz użyć `CSettingsStoreSP` klasy, aby przekierować wszystkie operacje rejestru MFC w innych lokalizacjach, takich jak plik XML lub bazy danych. W tym celu wykonaj następujące czynności:

1. Utwórz klasę (takie jak `CMyStore`) i pochodzić z `CSettingsStore`.

1. Użyj [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) i [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) makr z niestandardowych `CSettingsStore` klasy, aby umożliwić tworzenie dynamicznych.

1. Zastąpienia funkcji wirtualnych i zaimplementować `Read` i `Write` funkcji klasę niestandardową. Zaimplementuj inne funkcje, aby odczytywać i zapisywać dane do żądanej lokalizacji.

1. W aplikacji, należy wywołać `CSettingsStoreSP::SetRuntimeClass` i przekazać wskaźnik do [struktura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) uzyskanych od swojej klasy.

Zawsze wtedy, gdy struktura zazwyczaj może uzyskać dostępu do rejestru, wówczas teraz dynamicznie wystąpienia klasę niestandardową i użyć go do odczytywania i zapisywania danych.

`CSettingsStoreSP::SetRuntimeClass` używa statycznego zmiennej globalnej. W związku z tym tylko jeden magazyn niestandardowy jest dostępna w danym momencie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsettingsstore.h

##  <a name="create"></a>  CSettingsStoreSP::Create

Tworzy nowe wystąpienie obiektu, który jest tworzony na podstawie [klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bŚcieżka*<br/>
[in] Parametr logiczny, który określa, czy `CSettingsStore` obiekt zostanie utworzony w trybie administratora.

*bReadOnly*<br/>
[in] Parametr logiczny, który określa, czy `CSettingsStore` obiekt zostanie utworzony, aby uzyskać dostęp tylko do odczytu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do nowo utworzonego `CSettingsStore` obiektu.

### <a name="remarks"></a>Uwagi

Można użyć metody [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) Określanie typu obiektu `CSettingsStoreSP::Create` zostanie utworzony. Domyślnie ta metoda tworzy `CSettingsStore` obiektu.

Jeśli tworzysz `CSettingsStore` obiekt w trybie administratora, domyślna lokalizacja dla wszystkich dostęp do rejestru HKEY_LOCAL_MACHINE. W przeciwnym razie domyślną lokalizację dla wszystkich dostęp do rejestru jest HKEY_CURRENT_USER.

Jeśli *bŚcieżka* ma wartość TRUE, aplikacja musi mieć prawa administracyjne. W przeciwnym razie zakończy się niepowodzeniem podczas próby dostępu do rejestru.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `Create` metody `CSettingsStoreSP` klasy.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP

Konstruuje [klasa CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) obiektu.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
[in] Danych zdefiniowane przez użytkownika, `CSettingsStoreSP` obiektu magazynów.

### <a name="remarks"></a>Uwagi

`CSettingsStoreSP` Obiekt przechowuje dane z *dwUserData* w zmiennej chroniony element członkowski `m_dwUserData`.

##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass

Ustawia klasy środowiska uruchomieniowego. Metoda [CSettingsStoreSP::Create](#create) używa klasy środowiska uruchomieniowego, aby wyznaczyć, jakiego typu obiektu do utworzenia.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parametry

*pRTI*<br/>
[in] Wskaźnik do informacji o klasie czasu wykonywania dla klasy pochodnej z [klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; Wartość FALSE, jeśli klasa jest oznaczona *pRTI* nie pochodzi od `CSettingsStore`.

### <a name="remarks"></a>Uwagi

Możesz użyć [klasa CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) do wyprowadzenia klasy z `CSettingsStore`. Użyj metody `SetRuntimeClass` Jeśli chcesz utworzyć obiekty klasę niestandardową, która jest pochodną `CSettingsStore`.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md)
