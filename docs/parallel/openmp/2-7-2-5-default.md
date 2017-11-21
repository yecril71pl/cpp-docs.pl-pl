---
title: "2.7.2.5 domyślna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 26dff1f0e8b3b88b4891617a2eef2bb2d82240eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="2725-default"></a>2.7.2.5 — domyślne
**Domyślne** klauzuli zezwala użytkownikowi na wpływają na udostępnianie danych atrybutów, zmiennych. Składnia **domyślne** klauzuli wygląda następująco:  
  
```  
default(shared | none)  
```  
  
 Określanie **default(shared)** jest odpowiednikiem jawnie wyświetlania każdej zmiennej widoczne w **udostępnionego** klauzuli, chyba że jest **threadprivate** lub **cons**`t`-kwalifikowaną. W przypadku braku jawnego **domyślne** klauzuli, domyślne zachowanie jest taka sama jak w przypadku **default(shared)** zostały określone.  
  
 Określanie **default(none)** wymaga, że co najmniej jeden z następujących musi mieć wartość true dla każdego odwołania do zmiennej w zakresie leksykalne równoległych konstrukcja:  
  
-   Zmienna jawnie znajduje się w klauzuli udostępniania danych atrybutu konstrukcji, który zawiera odwołanie.  
  
-   Zmienna została zadeklarowana w ramach równoległego konstrukcji.  
  
-   Zmienna jest **threadprivate**.  
  
-   Nazwa zmiennej jest **const**-kwalifikowanego typu.  
  
-   Zmienna jest zmienna sterująca pętli dla **dla** pętli występujący natychmiast **dla** lub **równoległe w** dyrektywy i odwołanie do zmiennej pojawia się wewnątrz pętli .  
  
 Określenie zmiennej na **firstprivate**, **lastprivate**, lub **redukcji** klauzuli objętego dyrektywy powoduje niejawne odwołanie do zmiennej w załączonym kontekst. Takie niejawne odwołania są również wymaganiom wymienionych powyżej.  
  
 Tylko jeden **domyślne** można określić klauzuli **równoległych** dyrektywy.  
  
 Domyślna zmiennej atrybutu udostępniania danych może zostać przesłonięta przy użyciu **prywatnej**, **firstprivate**, **lastprivate**, **redukcji**, i **udostępnionego** klauzule, jak pokazano na poniższym przykładzie:  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```