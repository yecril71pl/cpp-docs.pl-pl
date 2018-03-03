---
title: "Hse_version_info — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 108f826ffaa17de65dafe246ab6724fac2b134f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO — Struktura
Ta struktura jest wskazywana przez `pVer` parametru w `CHttpServer::GetExtensionVersion` funkcję elementu członkowskiego. Zapewnia ISA numer wersji i opis ISA.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwExtensionVersion*  
 Numer wersji ISA.  
  
 *lpszExtensionDesc*  
 Opis tekstowy ISA. Domyślna implementacja zawiera tekst zastępczy; zastąpienie `CHttpServer::GetExtensionVersion` zapewnienie własny opis.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** httpext.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

