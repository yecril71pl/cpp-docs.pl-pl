---
title: Wejście i wyjście | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62319d040275d96314ee824f9fea020a4004974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389394"
---
# <a name="input-and-output"></a>Dane wejściowe i wyjściowe

Funkcje We/Wy odczytu i zapisu danych do i z plików i urządzeń. Operacje We/Wy pliku została wykonana w trybie tekst lub binarny. Biblioteka wykonawcza Microsoft zawiera trzy funkcje We/Wy:

- [We/Wy strumienia](../c-runtime-library/stream-i-o.md) funkcje traktować danych jako strumień znaki.

- [We/Wy niskiego poziomu](../c-runtime-library/low-level-i-o.md) systemu operacyjnego bezpośrednio dla operacji niższe niż te dostarczone przez we/wy strumienia wywołania funkcji.

- [Konsoli i portu We/Wy](../c-runtime-library/console-and-port-i-o.md) funkcji odczytu lub zapisu bezpośrednio w konsoli (klawiatury i ekranu), czy port We/Wy (na przykład port drukarki).

   > [!NOTE]
   > Ponieważ funkcje strumienia są buforowane, a nie są funkcje niskiego poziomu, te dwa typy funkcji są zazwyczaj niezgodne. Dla przetwarzania danego pliku, użyj wyłącznie strumienia lub funkcje niskiego poziomu.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
