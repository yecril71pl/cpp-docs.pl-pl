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
ms.openlocfilehash: daf1565c2fe2d7a4620f83b765671fea80502102
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335818"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO — Struktura
Ta struktura jest wskazywany przez *pVer* parametru w `CHttpServer::GetExtensionVersion` funkcja elementu członkowskiego. Zawiera numer wersji oprogramowania ISA i opis tekstowy ISA.  
  
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
 Opis tekstowy ISA. Domyślna implementacja zawiera tekst symbolu zastępczego; Zastąp `CHttpServer::GetExtensionVersion` zapewnienie własny opis.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** httpext.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

