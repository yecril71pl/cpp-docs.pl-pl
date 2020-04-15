---
title: Klasa CMenuTearOffManager
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: f41937179dc055213f3af093e107bcb08c8a8fcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369959"
---
# <a name="cmenutearoffmanager-class"></a>Klasa CMenuTearOffManager

Zarządza menu odrywu. Menu odrywu to menu na pasku menu. Użytkownik może usunąć menu odrywania z paska menu, powodując odrywanie menu float.

   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Konstruuje `CMenuTearOffManager` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenuTearOffManager::Kompilacja](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Inicjalizuj](#initialize)|Inicjuje `CMenuTearOffManager` obiekt.|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Uwagi

Aby można było korzystać z menu odrywać `CMenuTearOffManager` w aplikacji, musisz mieć obiekt. W większości przypadków nie będzie tworzyć ani `CMenuTearOffManager` inicjować obiektu bezpośrednio. Jest to obsługiwane dla Ciebie podczas wywoływania [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkcji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMenuTearOffManager` konstruować `CWinAppEX::EnableTearOffMenus` i inicjować obiekt, wywołując metodę. Ten fragment kodu jest częścią [przykładu word pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenutearoffmanager.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearOffManager::Kompilacja

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Parametry

[w] *uiTearOffBarID*<br/>

[w] *strText (tekst)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager

Konstruuje [obiekt CMenuTearOffManager.](../../mfc/reference/cmenutearoffmanager-class.md)

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie należy `CMenuTearOffManager` tworzyć ręcznie. Struktura aplikacji tworzy obiekt `CMenuTearOffManager` podczas wywoływania [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Inicjalizuj

Inicjuje [obiekt CMenuTearOffManager.](../../mfc/reference/cmenutearoffmanager-class.md)

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Parametry

*lpszRegEntry*<br/>
[w] Ciąg zawierający ścieżkę wpisu rejestru. Aplikacje przechowuje ustawienia dla odrywać paski w tym wpisie rejestru.

*uiTearOffMenuPier raz*<br/>
[w] Pierwszy identyfikator menu dla menu odrywu.

*uiTearOffMenuLast*<br/>
[w] Ostatni identyfikator menu dla menu odrywu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów menu od *uiTearOffMenuFirst* do *uiTearOffMenuLast* musi być ciągłym interwałem. Interwał definiuje liczbę menu odrywu, które mogą pojawić się w tym samym czasie w aplikacji.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Parametry

[w] *uiID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Parametry

[w] *ul.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Parametry

[w] *hmenu ( hmenu )*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *identyfikator uiCmdId*<br/>

[w] *bUżyzowanie*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

[w] *hMenu*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
