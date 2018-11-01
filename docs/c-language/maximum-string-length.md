---
title: Maksymalna długość ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: f2e5461c433a0d195682c1a0f4312a71a8ff5032
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483989"
---
# <a name="maximum-string-length"></a>Maksymalna długość ciągu

**Microsoft Specific**

Zgodność ANSI wymaga kompilatora do akceptowania 509 do znaków w literale ciągu po łączenia. Maksymalna długość literału ciągu znaków dozwolonych w Microsoft C to około 2048 bajtów. Jednak jeśli literał ciągu składa się z części ujęty w znaki podwójnego cudzysłowu, preprocesor łączy części w jeden ciąg i dla każdego wiersza połączonych dodaje dodatkowy bajt całkowitą liczbę bajtów.

Załóżmy na przykład, ciąg, który składa się z 40 wiersze z 50 znaków dla każdego wiersza (2000 znaków) i jeden wiersz 7 znaków, a każdy wiersz jest ujęty w podwójny cudzysłów. Spowoduje to dodanie maksymalnie 2,007 bajtów oraz jeden bajt kończącego znaku null dla danych całkowitych 2,008 bajtów. Na łączenia nadmiarowe znaki jest dodawany dla każdej linii najpierw 40. Dzięki temu daje w sumie 2048 bajtów. Należy pamiętać, jednak, że jeśli wierszy kontynuacji (\\) są używane zamiast znaki cudzysłowu, preprocesor nie powoduje dodania dodatkowych znaków dla każdego wiersza.

Gdy osoba ciąg w cudzysłowach nie może być dłuższa niż 2048 bajtów, literał ciągu około 65 535 bajtów można konstruować przez łączenie ciągów.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)