---
title: Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: a9e9df6b0bae49eaf599e56e5d96040afae315e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536568"
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