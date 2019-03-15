---
title: Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: e855b648dc7a9ee0670c3704a11aa1897a238403
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811917"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem

**__HrLoadAllImportsForDll** funkcji, która jest zdefiniowana w delayhlp.cpp, informuje konsolidator, aby załadować wszystkie Importy z biblioteki DLL, który został określony za pomocą [/delayload](delayload-delay-load-import.md) — opcja konsolidatora.

Importy Załaduj wszystko pozwala umieścić obsługi błędów w jednym miejscu w kodzie, a nie trzeba używać wyjątków, obsługa wokół rzeczywistego wywołania operacji importu. Unika również sytuacja, w którym aplikacji nie powiedzie się częściowo przez proces wyniku kod pomocniczy, nie można załadować importu.

Wywoływanie **__HrLoadAllImportsForDll** nie zmienia zachowanie punkty zaczepienia błąd przetwarzania; zobacz [obsługę błędów oraz powiadomienia](error-handling-and-notification.md) Aby uzyskać więcej informacji.

Nazwa biblioteki DLL są przekazywane do **__HrLoadAllImportsForDll** są porównywane nazwa przechowywana wewnątrz pliku DLL, sama i jest uwzględniana wielkość liter.

Poniższy przykład pokazuje sposób wywoływania **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
