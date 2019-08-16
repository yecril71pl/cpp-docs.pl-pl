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
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493117"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Określa zachowanie wyszukiwania manifestu.

## <a name="syntax"></a>Składnia

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Uwagi

**/ALLOWISOLATION** powoduje, że system operacyjny przeszukiwanie i ładowanie manifestu.

Wartość domyślna to **/ALLOWISOLATION** .

**/ALLOWISOLATION: nie** wskazuje, że pliki wykonywalne są ładowane tak, jakby nie było manifestu, i powoduje `DllCharacteristics` [odwołanie polecenia EDITBIN](editbin-reference.md) `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` do ustawiania bitu w polu opcjonalnego nagłówka.

Gdy izolacja jest wyłączona dla pliku wykonywalnego, moduł ładujący systemu Windows nie próbuje znaleźć manifestu aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślnego kontekstu aktywacji, nawet jeśli istnieje manifest w samym pliku wykonywalnym lub jeśli istnieje manifest o nazwie *Executable-Name*. exe. manifest.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Przeszukiwanie manifestu)](allowisolation-manifest-lookup.md)<br/>
[Dokumentacja plików manifestu](/windows/win32/SbsCs/manifest-files-reference)
