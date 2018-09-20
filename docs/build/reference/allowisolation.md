---
title: -ALLOWISOLATION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07414c86663ea6143a471691b01e584cdc033258
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392830"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Określa zachowanie wyszukiwania plików manifestu.

## <a name="syntax"></a>Składnia

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Uwagi

**/ ALLOWISOLATION** powoduje, że system operacyjny do manifestu, wyszukiwania i obciążeniami.

**/ ALLOWISOLATION** jest ustawieniem domyślnym.

**/ALLOWISOLATION:No** wskazuje, że pliki wykonywalne są ładowane tak, jakby nie było żadnych manifest i powoduje, że [odwołanie EDITBIN](../../build/reference/editbin-reference.md) można ustawić `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit w opcjonalnym nagłówku `DllCharacteristics` pola.

Po wyłączeniu izolacji dla pliku wykonywalnego modułu ładującego Windows nie spróbuj znaleźć manifest aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślny kontekst aktywacji, nawet jeśli istnieje manifest w pliku wykonywalnym, samego lub w przypadku manifestu, która ma nazwę *nazwę pliku wykonywalnego*. exe.manifest.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (Przeszukiwanie manifestu)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[Manifest plików — dokumentacja](/windows/desktop/SbsCs/manifest-files-reference)