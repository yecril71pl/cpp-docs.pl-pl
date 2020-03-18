---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440373"
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

**/ALLOWISOLATION: nie** wskazuje, że pliki wykonywalne są załadowane tak, jakby nie istniały manifest, i powoduje [odwołanie polecenia EDITBIN](editbin-reference.md) do ustawienia bitu `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` w polu `DllCharacteristics` nagłówka opcjonalnego.

Gdy izolacja jest wyłączona dla pliku wykonywalnego, moduł ładujący systemu Windows nie próbuje znaleźć manifestu aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślnego kontekstu aktywacji, nawet jeśli istnieje manifest w samym pliku wykonywalnym lub jeśli istnieje manifest o nazwie *Executable-Name*. exe. manifest.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Przeszukiwanie manifestu)](allowisolation-manifest-lookup.md)<br/>
[Dokumentacja plików manifestu](/windows/win32/SbsCs/manifest-files-reference)
