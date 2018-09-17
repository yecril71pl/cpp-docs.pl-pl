---
title: -ALLOWBIND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce0a33ebb0b8b9ba34ac241c8335e9524dec08b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715577"
---
# <a name="allowbind"></a>/ALLOWBIND

Określa, czy biblioteka DLL może być powiązana.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

**/ALLOWBIND** opcja ustawia bit w nagłówku biblioteki DLL, który wskazuje Bind.exe, że obraz może być powiązana. Powiązania umożliwiają obraz, aby ładować się szybciej, gdy moduł ładujący nie rebase i wykonywać naprawy adresów dla każdej biblioteki DLL, do którego istnieje odwołanie. Nie ma Biblioteka DLL była związana, jeśli jego została podpisana cyfrowo — powiązanie unieważnia podpis. Powiązania nie ma wpływu Jeśli randomizacji układu przestrzeni adresowej (ASLR) jest włączony dla obrazu za pomocą **opcja/DynamicBase** w wersjach systemu Windows, która obsługuje ASLR.

Użyj **/ALLOWBIND:NO** aby zapobiec Bind.exe powiązanie biblioteki DLL.

Aby uzyskać więcej informacji, zobacz [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) — opcja konsolidatora.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)