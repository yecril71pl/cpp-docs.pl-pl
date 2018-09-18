---
title: Magazynowanie adresów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe77d3775c489399bb8b9032e645eee17d70b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076596"
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów

Ilość miejsca wymaganego dla adresu i znaczenie adres są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie musi mieć tę samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.

**Microsoft Specific**

Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaracje wskaźników](../c-language/pointer-declarations.md)