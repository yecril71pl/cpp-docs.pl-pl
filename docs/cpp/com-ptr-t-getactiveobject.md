---
title: _com_ptr_t::GetActiveObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::GetActiveObject
dev_langs: C++
helpviewer_keywords: GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 153f7ffce400fd09e46706a361eebc87bbe1e1c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Dotyczące firmy Microsoft**  
  
 Dołącza do istniejącego wystąpienia obiektu podane **CLSID** lub **ProgID**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 **CLSID** obiektu.  
  
 `clsidString`  
 Ciąg Unicode, która przechowuje albo **CLSID** (począwszy od "**{**") lub **ProgID**.  
  
 `clsidStringA`  
 Ciąg wielobajtowy przy użyciu strony kodowej ANSI, którym jest przechowywana albo **CLSID** (począwszy od "**{**") lub **ProgID**.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie funkcji tych elementów członkowskich `GetActiveObject` pobrać wskaźnika do uruchomionego obiektu, który został zarejestrowany z OLE, a następnie typ interfejsu zapytania dotyczące wskaźnika inteligentnego. Wynikowa wskaźnika jest następnie hermetyzowany w ramach tego `_com_ptr_t` obiektu. **Wersja** jest wywoływana, aby zmniejszyć licznika odwołań do wcześniej hermetyzowany wskaźnika. Ta procedura zwraca `HRESULT` do wskazania powodzenia lub niepowodzenia.  
  
-   **GetActiveObject (**`rclsid`**)** dołącza do istniejącego wystąpienia obiektu podane **CLSID**.      
  
-   **GetActiveObject (**`clsidString`**)** dołącza do istniejącego wystąpienia obiektu podany ciąg Unicode, która przechowuje albo **CLSID** (począwszy od "**{**") lub **ProgID**.      
  
-   **GetActiveObject (**`clsidStringA`**)** dołącza do istniejącego wystąpienia obiektu podany ciąg znaków wielobajtowych, który przechowuje albo **CLSID** (począwszy od "**{**") lub **ProgID**.     Wywołania [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), który zakłada, że ten ciąg w stronę kodową ANSI zamiast strony kodowej OEM.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md)