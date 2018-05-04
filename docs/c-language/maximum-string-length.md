---
title: Maksymalna długość ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f95f4cb279c7e13d9500fbf5ce90a8ed82d55307
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="maximum-string-length"></a>Maksymalna długość ciągu
**Microsoft Specific**  
  
 Zgodność ANSI wymaga kompilatora, aby zaakceptować 509 do znaków w literale ciągu po łączenia. Maksymalna długość literału ciągu znaków dozwolonych w Microsoft C wynosi około 2048 bajtów. Jednak jeśli literał ciągu zawiera części ujęta w znaki cudzysłowu, preprocesora łączy części w jeden ciąg i dla każdego wiersza połączonych dodaje dodatkowy bajt całkowitą liczbę bajtów.  
  
 Załóżmy na przykład ciąg składa się z 40 wiersze z 50 znaków w wierszu (2000 znaków) i jeden wiersz z 7 znaków, a każdy wiersz jest ujęta w znaki podwójnego cudzysłowu. Spowoduje to dodanie do 2,007 bajtów oraz jeden bajt znak końcowy null dla danych całkowitych 2,008 bajtów. Na łączenia nadmiarowe znaki jest dodawany do każdego wiersza najpierw 40. Dzięki temu łącznie 2048 bajtów. Uwaga, jednak, że jeśli wiersz kontynuacje (\\) są używane zamiast znaki cudzysłowu, preprocesora nie dodaje dodatkowy znak dla każdego wiersza.  
  
 Gdy osoba ciąg nie może być dłuższa niż 2048 bajtów, literału ciągu około 65 535 bajtów można konstruować przez łączenie ciągów.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Literały ciągu języka C](../c-language/c-string-literals.md)