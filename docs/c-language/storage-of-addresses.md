---
title: Magazynowanie adresów
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 2a0e218d4d34fa1482986ecccd7da8adba38086b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539376"
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów

Ilość miejsca wymaganego dla adresu i znaczenie adres są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie musi mieć tę samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.

**Microsoft Specific**

Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaracje wskaźników](../c-language/pointer-declarations.md)