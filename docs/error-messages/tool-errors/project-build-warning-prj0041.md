---
title: "Ostrzeżenie prj0041 dotyczące kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0041
dev_langs: C++
helpviewer_keywords: PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e5a9d5fb5350e4ae6b33fc167aae14b1361291e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-warning-prj0041"></a>Ostrzeżenie PRJ0041 dotyczące kompilacji projektu
Nie można odnaleźć brakującej zależności 'zależności' dla pliku 'Plik'. Projekt może się skompilować poprawnie, ale mogą w dalszym ciągu oznaczony jako nieaktualny aż do znalezienia tego pliku.  
  
 Pliku (pliku zasobu lub.idl/.odl, na przykład zawierała instrukcję include, który system projektu nie można rozpoznać.  
  
 Ponieważ system projektów nie przetwarza instrukcje preprocesora (na przykład #if), ataku instrukcja może nie być faktycznie częścią kompilacji.  
  
 Aby usunąć to ostrzeżenie, usunąć wszystkie zbędne kodu w .RC — pliki lub Dodaj pliki symbolu zastępczego odpowiednią nazwę.