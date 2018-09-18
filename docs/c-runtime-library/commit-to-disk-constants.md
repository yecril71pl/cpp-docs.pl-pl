---
title: Stałe typu Commit-Disk | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- vc.constants
dev_langs:
- C++
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46ff21fec703069f9f3ac599d76e325d871a9744
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092924"
---
# <a name="commit-to-disk-constants"></a>Stałe typu commit-to-disk

**Microsoft Specific**

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Te stałe specyficzne dla firmy Microsoft Określ, czy bufor skojarzone z otwartego pliku jest opróżniany do buforów systemu operacyjnego lub na dysku. Tryb znajduje się w ciąg określający typ dostępu do odczytu/zapisu (**"r"**, **"w"**, **""**, **"r +"**, **"w +"** , **"+"**).

Tryby commit-to-disk są następujące:

- **c**

   Zapisuje zawartość niepisane określonego bufora na dysku. Ta funkcja commit-to-disk jest wykonywana wyłącznie w jawnych wywołań albo [fflush —](../c-runtime-library/reference/fflush.md) lub [_flushall —](../c-runtime-library/reference/flushall.md) funkcji. Ten tryb jest przydatny podczas pracy z danymi poufnymi. Na przykład, jeśli program kończy się po wywołaniu `fflush` lub `_flushall`, możesz mieć pewność, że dane z Tobą skontaktować bufory systemu operacyjnego. Jednakże chyba, że plik jest otwierany przy użyciu **c** opcji danych może nie należy wprowadzać je na dysku, jeśli system operacyjny także ulega zakończeniu.

- **N**

   Zapisuje zawartość niepisane określonego bufora bufory systemu operacyjnego. System operacyjny dane z pamięci podręcznej i następnie określić optymalny czas zapisu na dysku. W wielu okolicznościach to zachowanie sprawia, że program wydajne zachowania. Jednak w przypadku przechowywania danych krytycznych (np. transakcji bankowych lub informacje o bilecie linii lotniczych) należy wziąć pod uwagę przy użyciu **c** opcji. **n** tryb jest ustawieniem domyślnym.

> [!NOTE]
> **c** i **n** opcje nie są częścią standardu ANSI `fopen`, ale są rozszerzenia Microsoft i nie powinna być używana gdzie pożądana jest przenośność kodowania ANSI.

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Za pomocą funkcji Commit-to-Disk przy użyciu istniejącego kodu

Domyślnie wywołuje w celu [fflush —](../c-runtime-library/reference/fflush.md) lub [_flushall —](../c-runtime-library/reference/flushall.md) funkcji biblioteki zapisu danych do buforów obsługiwanego przez system operacyjny. System operacyjny określa optymalny czas faktycznie zapisywać dane na dysku. Funkcja commit-to-disk biblioteki wykonawczej pozwala upewnić się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Możesz udzielić tej możliwości do istniejących programów bez ponownego zapisywania adresów, łącząc swoje pliki obiektów z plikiem COMMODE.OBJ.

Wynikowy plik wykonywalny wywołuje w celu `fflush` zapisywanie zawartości buforu bezpośrednio z dysku i wywołania `_flushall` zapisywanie zawartości wszystkich buforów na dysku. Te dwie funkcje są jedynymi osobami wpływ z plikiem COMMODE.OBJ.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Stream operacji We/Wy](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
