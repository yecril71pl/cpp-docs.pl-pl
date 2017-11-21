---
title: _com_ptr_t::CreateInstance | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::CreateInstance
dev_langs: C++
helpviewer_keywords: CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73048093c35fe28bf02af60d6b99963df8394dc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Dotyczące firmy Microsoft**  
  
 Tworzy nowe wystąpienie obiektu podane **CLSID** lub **ProgID**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 **CLSID** obiektu.  
  
 `clsidString`  
 Ciąg Unicode, która przechowuje albo **CLSID** (począwszy od "**{**") lub **ProgID**.  
  
 `clsidStringA`  
 Ciąg wielobajtowy przy użyciu strony kodowej ANSI, którym jest przechowywana albo **CLSID** (począwszy od "**{**") lub **ProgID**.  
  
 `dwClsContext`  
 Kontekst do uruchomienia kodu wykonywalnego.  
  
 `pOuter`  
 Zewnętrzne nieznany dla [agregacji](../atl/aggregation.md).  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie funkcji tych elementów członkowskich `CoCreateInstance` do utworzenia nowego obiektu modelu COM, a następnie zapytania dla typu interfejsu wskaźnika inteligentnego. Wynikowa wskaźnika jest następnie hermetyzowany w ramach tego `_com_ptr_t` obiektu. **Wersja** jest wywoływana, aby zmniejszyć licznika odwołań do wcześniej hermetyzowany wskaźnika. Ta procedura zwraca `HRESULT` do wskazania powodzenia lub niepowodzenia.  
  
-   **CreateInstance (** `rclsid` **,**`dwClsContext`**)** tworzy nowe wystąpienie uruchomionych danego obiektu **CLSID**.        
  
-   **CreateInstance (** `clsidString` **,**`dwClsContext`**)** tworzy uruchomione nowe wystąpienie obiektu podany ciąg Unicode, która przechowuje albo **CLSID** (począwszy od "**{**") lub **ProgID**.        
  
-   **CreateInstance (** `clsidStringA` **,**`dwClsContext`**)** tworzy uruchomione nowe wystąpienie obiektu podany ciąg znaków wielobajtowych, który przechowuje albo  **Identyfikator CLSID** (począwszy od "**{**") lub **ProgID**.       Wywołania [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), który zakłada, że ten ciąg w stronę kodową ANSI zamiast strony kodowej OEM.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md)