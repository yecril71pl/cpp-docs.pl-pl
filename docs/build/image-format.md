---
title: Obraz formatu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715419"
---
# <a name="image-format"></a>Format obrazu

Format obrazu pliku wykonywalnego jest je typu PE32 +. Obrazy wykonywalne (plików dll i exe) są ograniczone do maksymalnie 2 GB, więc względne adresowanie z 32-bitowe przesunięcie może służyć do danych obraz statyczny adres. Te dane obejmują tabeli adresów importowania, stałe typu string, statycznych danych globalnych i tak dalej.

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)