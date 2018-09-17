---
title: Klasa CMenuTearOffManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ca3af6aba4c208672038de2ca663efdb2cc9d9a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700937"
---
# <a name="cmenutearoffmanager-class"></a>Klasa CMenuTearOffManager
Zarządza menu odrywania. Menu odrywania jest menu na pasku menu. Użytkownik może usunąć zrywalne menu z paska menu, powodując unoszenie się menu zrywalnego.  
  
   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
   
## <a name="syntax"></a>Składnia  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Konstruuje `CMenuTearOffManager` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|Inicjuje `CMenuTearOffManager` obiektu.|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>Uwagi  
 Aby można było używać zrywanie menu w aplikacji, konieczne jest posiadanie `CMenuTearOffManager` obiektu. W większości przypadków nie będzie Tworzenie lub zainicjować `CMenuTearOffManager` obiektu bezpośrednio. Jest to obsługiwane za Ciebie, po wywołaniu [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i zainicjować `CMenuTearOffManager` obiektu przez wywołanie metody `CWinAppEX::EnableTearOffMenus` metody. Ten fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmenutearoffmanager.h  
  
##  <a name="build"></a>  CMenuTearOffManager::Build  

  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
*uiTearOffBarID*<br/>
[in] [in] *strText*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager  
 Konstruuje [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) obiektu.  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków nie należy tworzyć `CMenuTearOffManager` ręcznie. Szablon aplikacja tworzy `CMenuTearOffManager` obiektu po wywołaniu [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).  
  
##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath  

  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="initialize"></a>  CMenuTearOffManager::Initialize  
 Inicjuje [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) obiektu.  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>Parametry  
*lpszRegEntry*<br/>
[in] Ciąg, który zawiera ścieżkę wpisu rejestru. Aplikacje są przechowywane ustawienia odrywania słupków tego wpisu rejestru.  
  
*uiTearOffMenuFirst*<br/>
[in] Pierwszy identyfikator menu menu odrywania.  
  
*uiTearOffMenuLast*<br/>
[in] Identyfikator ostatniego menu do menu odrywania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zakres identyfikatorów menu z *uiTearOffMenuFirst* do *uiTearOffMenuLast* musi być ciągłe interwału. Interwał definiuje liczbę menu odrywania, które mogą być wyświetlane w tym samym czasie w aplikacji.  
  
##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID  

  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiID*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="parse"></a>  CMenuTearOffManager::Parse  

  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *str*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="reset"></a>  CMenuTearOffManager::Reset  

  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hmenu*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse  

  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmdId*<br/>
[in] [in] *bUżyj*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus  

  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hMenu*  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
