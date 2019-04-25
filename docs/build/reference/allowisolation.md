---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 02012e7561fe8462f5f25ae13d961c35561666ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273147"
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

**/ALLOWISOLATION:No** wskazuje, że pliki wykonywalne są ładowane tak, jakby nie było żadnych manifest i powoduje, że [odwołanie EDITBIN](editbin-reference.md) można ustawić `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit w opcjonalnym nagłówku `DllCharacteristics` pola.

Po wyłączeniu izolacji dla pliku wykonywalnego modułu ładującego Windows nie spróbuj znaleźć manifest aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślny kontekst aktywacji, nawet jeśli istnieje manifest w pliku wykonywalnym, samego lub w przypadku manifestu, która ma nazwę *nazwę pliku wykonywalnego*. exe.manifest.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Przeszukiwanie manifestu)](allowisolation-manifest-lookup.md)<br/>
[Manifest plików — dokumentacja](/windows/desktop/SbsCs/manifest-files-reference)
