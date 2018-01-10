---
title: Klasa CMenuTearOffManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efb1b7acc2f4eb779de49559b5b566e89d518a0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmenutearoffmanager-class"></a>Klasa CMenuTearOffManager
Zarządza oderwania menu. Menu oderwania jest menu na pasku menu. Użytkownik może usunąć menu oderwania z menu paska menu oderwania float powoduje.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
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
 Aby można było używać oderwania menu w aplikacji, musi mieć `CMenuTearOffManager` obiektu. W większości przypadków, nie będzie utworzyć lub zainicjować `CMenuTearOffManager` obiekt bezpośrednio. To jest już obsługiwane podczas wywoływania [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak utworzyć i zainicjuj `CMenuTearOffManager` obiektu przez wywołanie metody `CWinAppEX::EnableTearOffMenus` metody. Następujący fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmenutearoffmanager.h  
  
##  <a name="build"></a>CMenuTearOffManager::Build  

  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiTearOffBarID`  
 [in]`strText`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager  
 Konstruuje [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) obiektu.  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków, nie należy tworzyć `CMenuTearOffManager` ręcznie. Struktura aplikacji tworzy `CMenuTearOffManager` obiektu po wywołaniu [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).  
  
##  <a name="getregpath"></a>CMenuTearOffManager::GetRegPath  

  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="initialize"></a>CMenuTearOffManager::Initialize  
 Inicjuje [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) obiektu.  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszRegEntry`  
 Ciąg, który zawiera ścieżkę wpisu rejestru. Aplikacje przechowuje ustawienia oderwania paski w ten wpis rejestru.  
  
 [in]`uiTearOffMenuFirst`  
 Pierwszy identyfikator menu dla menu oderwania.  
  
 [in]`uiTearOffMenuLast`  
 Identyfikator ostatniego menu dla menu oderwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zakres identyfikatorów menu z `uiTearOffMenuFirst` do `uiTearOffMenuLast` musi być ciągłe interwału. Interwał definiuje kilka kolejnych menu oderwania, które mogą być wyświetlane w tym samym czasie w aplikacji.  
  
##  <a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID  

  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="parse"></a>CMenuTearOffManager::Parse  

  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`str`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="reset"></a>CMenuTearOffManager::Reset  

  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hmenu`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setinuse"></a>CMenuTearOffManager::SetInUse  

  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdId`  
 [in]`bUse`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus  

  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hMenu`  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
