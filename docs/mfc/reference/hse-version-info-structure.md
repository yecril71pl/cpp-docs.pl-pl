---
title: HSE_VERSION_INFO — Struktura
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 6bdb668be037dfaa07e1121e4b61ea332e430e31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577295"
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

*dwExtensionVersion*<br/>
Numer wersji ISA.

*lpszExtensionDesc*<br/>
Opis tekstowy ISA. Domyślna implementacja zawiera tekst symbolu zastępczego; Zastąp `CHttpServer::GetExtensionVersion` zapewnienie własny opis.

## <a name="requirements"></a>Wymagania

**Nagłówek:** httpext.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

