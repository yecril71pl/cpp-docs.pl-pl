---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4cb7e5a3627d865e2f2193dee096c72cced75f5f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819821"
---
# <a name="allowbind"></a>/ALLOWBIND

Określa, czy biblioteka DLL może być powiązana.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

**/ALLOWBIND** opcja ustawia bit w nagłówku biblioteki DLL, który wskazuje Bind.exe, że obraz może być powiązana. Powiązania umożliwiają obraz, aby ładować się szybciej, gdy moduł ładujący nie rebase i wykonywać naprawy adresów dla każdej biblioteki DLL, do którego istnieje odwołanie. Nie ma Biblioteka DLL była związana, jeśli jego została podpisana cyfrowo — powiązanie unieważnia podpis. Powiązania nie ma wpływu Jeśli randomizacji układu przestrzeni adresowej (ASLR) jest włączony dla obrazu za pomocą **opcja/DynamicBase** w wersjach systemu Windows, która obsługuje ASLR.

Użyj **/ALLOWBIND:NO** aby zapobiec Bind.exe powiązanie biblioteki DLL.

Aby uzyskać więcej informacji, zobacz [/ALLOWBIND](allowbind-prevent-dll-binding.md) — opcja konsolidatora.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)
