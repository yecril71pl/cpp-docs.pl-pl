---
title: Zalety i wady metody używanej do tworzenia linków do CRT
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: b2e504de91cea9fef6e9acb0fc851bc2cc271e97
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221278"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Zalety i wady metody używanej do tworzenia linków do CRT

Projekt można połączyć z CRT, dynamicznie lub statycznie. W poniższej tabeli przedstawiono zalety i wady związane z wybór metody do użycia.

|Metoda|Korzyść|Kosztem|
|------------|-------------|--------------|
|Statycznie łączenie CRT<br /><br /> (**Biblioteki środowiska uruchomieniowego** równa **apartamentem**)|Biblioteka DLL CRT nie jest wymagane w systemie, w którym będzie uruchamiany obrazu.|Około 25 tys uruchamiania kodu jest dodawany do obrazu systemu znaczne zwiększenie jego rozmiaru.|
|Dynamiczne łączenie CRT<br /><br /> (**Biblioteki środowiska uruchomieniowego** równa **wielowątkowych**)|Obraz nie wymaga kod uruchamiający CRT, więc jest znacznie mniejszy.|Biblioteka DLL CRT musi być w systemem obrazu.|

Temat [łączenie CRT w ATL projektu](../atl/linking-to-the-crt-in-your-atl-project.md) w tym artykule omówiono sposób wybierania sposobu, w jaki połączyć CRT.

## <a name="see-also"></a>Zobacz także

[Programowanie za pomocą kodu ATL i C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Zachowanie biblioteki wykonawczej DLL i Visual C++](../build/run-time-library-behavior.md)<br/>
[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
