---
title: "Arytmetyczny wskaźnik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94f18b8a81cfde8d45a4e9e0256dd99a21bdd6a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pointer-arithmetic"></a>Arytmetyczny wskaźnik
Operacje dodawania obejmująca wskaźnik i całkowitą nadaj znaczące wyniki tylko wtedy, gdy argumentem wskaźnika dotyczy elementu członkowskiego tablicy i wartość całkowita tworzy przesunięcie w granicach tej samej tablicy. Wartość całkowita przekonwertowany do przesunięcia adres kompilator zakłada, czy tylko pamięci stanowisk ten sam rozmiar mieszczą się pomiędzy oryginalnego adresu i adres oraz przesunięcie.  
  
 To założenie jest prawidłowy dla tablicy elementów członkowskich. Zgodnie z definicją tablicy jest szereg wartości tego samego typu; jego elementy znajdują się w lokalizacji pamięci ciągłej. Magazyn dla wszystkich typów, z wyjątkiem elementów tablicy nie jest gwarantowana zostać wypełnione przez ten sam typ identyfikatorów. Oznacza to puste mogą występować między pozycji pamięci, nawet położenia tego samego typu. W związku z tym wyniki dodawanie do lub usuwanie adresy wartości, ale elementy tablicy jest nieokreślona.  
  
 Podobnie po odjęciu są dwie wartości wskaźnika, konwersja przyjęto założenie, że tylko wartości tego samego typu, o niepuste, mieszczą się pomiędzy adresy podane przez argumenty operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)