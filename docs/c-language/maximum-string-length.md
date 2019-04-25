---
title: Maksymalna długość ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 650088249e4c6abd515c29b873a9f09dc1d2a60a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232881"
---
# <a name="maximum-string-length"></a>Maksymalna długość ciągu

**Microsoft Specific**

Zgodność ANSI wymaga kompilatora do akceptowania 509 do znaków w literale ciągu po łączenia. Maksymalna długość literału ciągu znaków dozwolonych w Microsoft C to około 2048 bajtów. Jednak jeśli literał ciągu składa się z części ujęty w znaki podwójnego cudzysłowu, preprocesor łączy części w jeden ciąg i dla każdego wiersza połączonych dodaje dodatkowy bajt całkowitą liczbę bajtów.

Załóżmy na przykład, ciąg, który składa się z 40 wiersze z 50 znaków dla każdego wiersza (2000 znaków) i jeden wiersz 7 znaków, a każdy wiersz jest ujęty w podwójny cudzysłów. Spowoduje to dodanie maksymalnie 2,007 bajtów oraz jeden bajt kończącego znaku null dla danych całkowitych 2,008 bajtów. Na łączenia nadmiarowe znaki jest dodawany dla każdej linii najpierw 40. Dzięki temu daje w sumie 2048 bajtów. Należy pamiętać, jednak, że jeśli wierszy kontynuacji (\\) są używane zamiast znaki cudzysłowu, preprocesor nie powoduje dodania dodatkowych znaków dla każdego wiersza.

Gdy osoba ciąg w cudzysłowach nie może być dłuższa niż 2048 bajtów, literał ciągu około 65 535 bajtów można konstruować przez łączenie ciągów.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Literały ciągu języka C](../c-language/c-string-literals.md)
