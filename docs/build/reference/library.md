---
title: BIBLIOTEKA
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811787"
---
# <a name="library"></a>BIBLIOTEKA

/ ORDER informuje KONSOLIDACJĘ, aby utworzyć biblioteki DLL. W tym samym czasie LINK tworzy bibliotekę importu, chyba że używany jest plik .exp w kompilacji.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Uwagi

*Biblioteki* argument określa nazwę biblioteki DLL. Można również użyć [/OUT](out-output-file-name.md) opcję konsolidatora, aby określić nazwę wyjściowego pliku DLL.

Podstawa =*adres* argument ustawia adres podstawowy, który korzysta z systemu operacyjnego można załadować biblioteki DLL. Argument ten zastępuje domyślną lokalizację biblioteki DLL 0x10000000. Zobacz opis [/BASE](base-base-address.md) opcji szczegółowe informacje na temat adres podstawowy.

Pamiętaj, aby używać [/dll](dll-build-a-dll.md) podczas kompilowania biblioteki DLL — opcja konsolidatora.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
