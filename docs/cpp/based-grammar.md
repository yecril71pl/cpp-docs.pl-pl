---
title: __based — gramatyka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d1713b0cc8e1d5d53d3b30f3dd48a0b54a3782
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401964"
---
# <a name="based-grammar"></a>__based — Gramatyka
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Adresowanie na podstawie jest przydatne, gdy będziesz potrzebować precyzyjną kontrolę nad tym segment, w których obiekty są przydzielane (statycznych i dynamicznych na podstawie danych).  
  
 Tylko formularza na podstawie adresowania dopuszczalne w kompilacjach kodu 32-bitowych i 64-bitowy "opiera się na wskaźnik", który definiuje typ, który zawiera 32-bitową lub 64-bitowe przesunięcie podstawowy 32-bitową lub 64-bitowe lub oparte na **void**.  
  
## <a name="grammar"></a>Gramatyka  
 *na podstawie zakresu — modyfikator*:  
 **__based (***base-expression***)**   
  
 *wyrażenie Base*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-CAST*  
  
 *na podstawie zmiennej*:  
 *Identyfikator*  
  
 *na podstawie abstrakcyjny declarator*:  
 *deklarator abstrakcyjny*  
  
 *typem podstawowym*:  
 *Nazwa typu*  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Wskaźniki bazowe](../cpp/based-pointers-cpp.md)