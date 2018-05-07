---
title: Ostrzeżenie prj0041 dotyczące kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e845967b0a7116d6edade98b571de5bc1bcd9a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-warning-prj0041"></a>Ostrzeżenie PRJ0041 dotyczące kompilacji projektu
Nie można odnaleźć brakującej zależności 'zależności' dla pliku 'Plik'. Projekt może się skompilować poprawnie, ale mogą w dalszym ciągu oznaczony jako nieaktualny aż do znalezienia tego pliku.  
  
 Pliku (pliku zasobu lub.idl/.odl, na przykład zawierała instrukcję include, który system projektu nie można rozpoznać.  
  
 Ponieważ system projektów nie przetwarza instrukcje preprocesora (na przykład #if), ataku instrukcja może nie być faktycznie częścią kompilacji.  
  
 Aby usunąć to ostrzeżenie, usunąć wszystkie zbędne kodu w .RC — pliki lub Dodaj pliki symbolu zastępczego odpowiednią nazwę.