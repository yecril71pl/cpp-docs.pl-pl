---
title: Hse_version_info — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acdf63e062aab1407daee461e22f00f5d3c59cee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369889"
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

