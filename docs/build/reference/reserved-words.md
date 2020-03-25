---
title: Słowa zastrzeżone
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171154"
---
# <a name="reserved-words"></a>Słowa zastrzeżone

Następujące słowa są zastrzeżone przez konsolidator. Te nazwy mogą być używane jako argumenty w [instrukcjach definicji modułów](module-definition-dot-def-files.md) tylko wtedy, gdy nazwa jest ujęta w znaki podwójnego cudzysłowu ("").

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**Ładuj**|
|**OPIERA**|**IOPL**|**UŻYTEK**|
|**KODU**|**Biblioteka**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**NIEZGODNEJ**|**LOADONCALL**<sup>1</sup>|**Czysty**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**TRYBIE**|
|**ZHARMONIZOWAN**|**MOVABLE**<sup>1</sup>|**READWRITE**|
|**DEV386**|**Ruchome**<sup>1</sup>|Liczba **rzeczywista**<sup>1</sup>|
|**Odrzucanie**|**WIELOKROTN**|**REZYDENCI**|
|**DYNAMICZNYCH**|**NAZWIJ**|**Rezydentname**<sup>1</sup>|
|**TYLKO DO WYKONANIA**|**NEWFILES**<sup>2</sup>|**POSZCZEGÓLNE**|
|**EXECUTEONLY**|Brak **danych**<sup>1</sup>|**ODCINK**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**UDOSTĘPNIAĆ**|
|**EXETYPE**|**NONAME**|**WIERSZ**|
|**EXPORTS**|**Niezgodne**<sup>1</sup>|**STACKSIZE**|
|**Stała**<sup>1</sup>|**Odrzucane**|**STUB**|
|**Funkcje**<sup>2</sup>|**DAWAJ**|**Wersja**|
|**HEAPSIZE**|**NIEUDOSTĘPNIONYCH**|**WINDOWAPI**|
|**IMPORTOWANIA**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**Nieczysty**<sup>1</sup>|**ELEMENTY**|**Systemy**|
|**Uwzględnij**<sup>2</sup>|**Stary**<sup>1</sup>||

<sup>1</sup> konsolidator emituje ostrzeżenie ("zignorowano") w momencie napotkania tego terminu. Jednak słowo jest nadal zarezerwowane.

<sup>2</sup> konsolidator ignoruje ten wyraz, ale nie emituje ostrzeżenia.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
