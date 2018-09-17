---
title: Importy Załaduj wszystko dla bibliotek DLL ładowanych z opóźnieniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ef1c576af7930e157dafd0f57bf0b8dff49fa6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715588"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem

**__HrLoadAllImportsForDll** funkcji, która jest zdefiniowana w delayhlp.cpp, informuje konsolidator, aby załadować wszystkie Importy z biblioteki DLL, który został określony za pomocą [/delayload](../../build/reference/delayload-delay-load-import.md) — opcja konsolidatora.

Importy Załaduj wszystko pozwala umieścić obsługi błędów w jednym miejscu w kodzie, a nie trzeba używać wyjątków, obsługa wokół rzeczywistego wywołania operacji importu. Unika również sytuacja, w którym aplikacji nie powiedzie się częściowo przez proces wyniku kod pomocniczy, nie można załadować importu.

Wywoływanie **__HrLoadAllImportsForDll** nie zmienia zachowanie punkty zaczepienia błąd przetwarzania; zobacz [obsługę błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md) Aby uzyskać więcej informacji.

Nazwa biblioteki DLL są przekazywane do **__HrLoadAllImportsForDll** są porównywane nazwa przechowywana wewnątrz pliku DLL, sama i jest uwzględniana wielkość liter.

Poniższy przykład pokazuje sposób wywoływania **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Zobacz też

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)