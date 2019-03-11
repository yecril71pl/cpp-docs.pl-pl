---
title: Dane wejściowe i wyjściowe
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
ms.openlocfilehash: 2669ed3437fe0eea7dd648367feabe66ae6ed6d4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738515"
---
# <a name="input-and-output"></a>Dane wejściowe i wyjściowe

Funkcje We/Wy odczytu i zapisu danych do i z plików i urządzeń. Operacje We/Wy na plikach odbywać się w trybie tekstu lub w trybie binarnym. Biblioteki wykonawczej firmy Microsoft dostępne są trzy typy operacji We/Wy funkcji:

- [Stream operacji We/Wy](../c-runtime-library/stream-i-o.md) funkcje traktowanie danych jako strumień pojedynczych znaków.

- [Niskiego poziomu operacji We/Wy](../c-runtime-library/low-level-i-o.md) wywołają procedurę obsługi systemu operacyjnego bezpośrednio do operacji niższe niż te dostarczone przez strumień we/wy.

- [Konsoli i portu We/Wy](../c-runtime-library/console-and-port-i-o.md) funkcji Odczyt lub zapis bezpośrednio do konsoli (klawiatury i ekran) lub portu We/Wy (na przykład portu drukarki).

   > [!NOTE]
   > Ponieważ funkcje strumienia są buforowane i nie są funkcje niskiego poziomu, te dwa typy funkcji są zazwyczaj niezgodne. Dla przetwarzania danego pliku, użyj wyłącznie strumienia lub funkcji niskiego poziomu.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
