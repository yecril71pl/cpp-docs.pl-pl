---
title: Magazynowanie adresów
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148741"
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów

Ilość miejsca wymaganego dla adresu i znaczenie adres są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie musi mieć tę samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.

**Microsoft Specific**

Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaracje wskaźników](../c-language/pointer-declarations.md)
