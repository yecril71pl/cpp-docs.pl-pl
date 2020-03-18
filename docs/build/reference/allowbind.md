---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440389"
---
# <a name="allowbind"></a>/ALLOWBIND

Określa, czy można powiązać bibliotekę DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

Opcja **/ALLOWBIND** ustawia bit w nagłówku dll, który wskazuje na powiązanie. exe, że obraz może być powiązany. Powiązanie może umożliwić szybsze ładowanie obrazu, gdy moduł ładujący nie musi zmienić bazy i wykonać naprawy adresu dla każdej biblioteki DLL, do której się odwołuje. Nie ma potrzeby powiązania DLL, jeśli został on podpisany cyfrowo — powiązanie unieważnia sygnaturę. Powiązanie nie ma wpływu, jeśli jest włączone generowanie losowe układu przestrzeni adresowej (ASLR) dla obrazu za pomocą **/DYNAMICBASE** w wersjach systemu Windows, które obsługują ASLR.

Użyj **/ALLOWBIND: nie** , aby zapobiec powiązaniu pliku DLL przez program bind. exe.

Aby uzyskać więcej informacji, zobacz [/ALLOWBIND](allowbind-prevent-dll-binding.md) — opcja konsolidatora.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)
