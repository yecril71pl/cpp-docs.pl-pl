---
title: "Maksymalna długość ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa558129368559f3edddf9037f7f504933eb2563
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="maximum-string-length"></a>Maksymalna długość ciągu
**Dotyczące firmy Microsoft**  
  
 Zgodność ANSI wymaga kompilatora, aby zaakceptować 509 do znaków w literale ciągu po łączenia. Maksymalna długość literału ciągu znaków dozwolonych w Microsoft C wynosi około 2048 bajtów. Jednak jeśli literał ciągu zawiera części ujęta w znaki cudzysłowu, preprocesora łączy części w jeden ciąg i dla każdego wiersza połączonych dodaje dodatkowy bajt całkowitą liczbę bajtów.  
  
 Załóżmy na przykład ciąg składa się z 40 wiersze z 50 znaków w wierszu (2000 znaków) i jeden wiersz z 7 znaków, a każdy wiersz jest ujęta w znaki podwójnego cudzysłowu. Spowoduje to dodanie do 2,007 bajtów oraz jeden bajt znak końcowy null dla danych całkowitych 2,008 bajtów. Na łączenia nadmiarowe znaki jest dodawany do każdego wiersza najpierw 40. Dzięki temu łącznie 2048 bajtów. Uwaga, jednak, że jeśli wiersz kontynuacje (\\) są używane zamiast znaki cudzysłowu, preprocesora nie dodaje dodatkowy znak dla każdego wiersza.  
  
 Gdy osoba ciąg nie może być dłuższa niż 2048 bajtów, literału ciągu około 65 535 bajtów można konstruować przez łączenie ciągów.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Literały ciągu języka C](../c-language/c-string-literals.md)