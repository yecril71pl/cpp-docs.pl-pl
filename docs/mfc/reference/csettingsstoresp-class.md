---
title: Klasa CSettingsStoreSP
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318453"
---
# <a name="csettingsstoresp-class"></a>Klasa CSettingsStoreSP

Klasa `CSettingsStoreSP` jest klasą pomocniczą, której można użyć do tworzenia wystąpień [klasy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="syntax"></a>Składnia

```
class CSettingsStoreSP
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Konstruuje `CSettingsStoreSP` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSettingsStoreSP::Tworzenie](#create)|Tworzy wystąpienie klasy, która pochodzi `CSettingsStore`od .|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Ustawia klasę środowiska wykonawczego. Metoda `Create` używa klasy środowiska wykonawczego, aby określić, jaką klasę obiektów do utworzenia.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_dwUserData`|Niestandardowe dane użytkownika, `CSettingsStoreSP` które są przechowywane w obiekcie. Te dane są poprzedne `CSettingsStoreSP` w konstruktorze obiektu.|
|`m_pRegistry`|Obiekt `CSettingsStore`pochodny, który `Create` tworzy metoda.|

## <a name="remarks"></a>Uwagi

`CSettingsStoreSP` Klasy można użyć do przekierowania wszystkich operacji rejestru MFC do innych lokalizacji, takich jak plik XML lub bazy danych. W tym celu wykonaj następujące kroki:

1. Utwórz klasę (na `CMyStore`przykład) i `CSettingsStore`wywodź ją z .

1. Użyj [makr DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) i [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) z klasą niestandardową, `CSettingsStore` aby umożliwić tworzenie dynamiczne.

1. Zastądnik funkcji wirtualnych i zaimplementuj `Read` funkcje i `Write` funkcje w klasie niestandardowej. Zaimplementuj inne funkcje do odczytu i zapisu danych w żądanej lokalizacji.

1. W aplikacji wywołać `CSettingsStoreSP::SetRuntimeClass` i przekazać w wskaźnik do [CRuntimeClass Struktury](../../mfc/reference/cruntimeclass-structure.md) uzyskane z klasy.

Za każdym razem, gdy struktura zazwyczaj uzyskiwać dostęp do rejestru, będzie teraz dynamicznie tworzyć wystąpienia klasy niestandardowej i używać jej do odczytu lub zapisu danych.

`CSettingsStoreSP::SetRuntimeClass`używa globalnej zmiennej statycznej. W związku z tym tylko jeden magazyn niestandardowy jest dostępny w czasie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP::Tworzenie

Tworzy nowe wystąpienie obiektu, który jest pochodną [CSettingsStore Klasy](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bDmin*<br/>
[w] Parametr logiczny określający, `CSettingsStore` czy obiekt jest tworzony w trybie administratora.

*bCzytyNie*<br/>
[w] Parametr logiczny, który określa, czy `CSettingsStore` obiekt jest tworzony dla dostępu tylko do odczytu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do nowo `CSettingsStore` utworzonego obiektu.

### <a name="remarks"></a>Uwagi

Metody [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) można użyć, aby określić, jaki typ obiektu `CSettingsStoreSP::Create` utworzy. Domyślnie ta metoda `CSettingsStore` tworzy obiekt.

Jeśli obiekt `CSettingsStore` zostanie utworzony w trybie administratora, domyślną lokalizacją dla całego dostępu do rejestru jest HKEY_LOCAL_MACHINE. W przeciwnym razie domyślną lokalizacją dla całego dostępu do rejestru jest HKEY_CURRENT_USER.

Jeśli *bAdmin* ma wartość TRUE, aplikacja musi mieć prawa administracyjne. W przeciwnym razie zakończy się niepowodzeniem, gdy próbuje uzyskać dostęp do rejestru.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `Create` metody `CSettingsStoreSP` klasy.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP

Konstruuje [CSettingsStoreSP Class](../../mfc/reference/csettingsstoresp-class.md) obiektu.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
[w] Dane zdefiniowane przez `CSettingsStoreSP` użytkownika, które przechowuje obiekt.

### <a name="remarks"></a>Uwagi

Obiekt `CSettingsStoreSP` przechowuje dane z *dwUserData* w `m_dwUserData`chronionej zmiennej członkowskiej .

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass

Ustawia klasę środowiska wykonawczego. Metoda [CSettingsStoreSP::Create](#create) używa klasy środowiska wykonawczego, aby określić, jaki typ obiektu do utworzenia.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parametry

*pRTI*<br/>
[w] Wskaźnik do informacji o klasie środowiska wykonawczego dla klasy pochodnej [klasy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; FALSE, jeśli klasa zidentyfikowana przez *pRTI* nie jest pochodną `CSettingsStore`.

### <a name="remarks"></a>Uwagi

[CSettingsStoreSP Class](../../mfc/reference/csettingsstoresp-class.md) można użyć do uzyskania `CSettingsStore`klas z . Użyj metody, `SetRuntimeClass` jeśli chcesz utworzyć obiekty klasy niestandardowej, `CSettingsStore`która pochodzi od .

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md)
