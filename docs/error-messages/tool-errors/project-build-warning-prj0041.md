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
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038142"
---
# <a name="project-build-warning-prj0041"></a>Ostrzeżenie PRJ0041 dotyczące kompilacji projektu

Nie można odnaleźć brakującej zależności 'zależności' dla pliku 'Plik'. Projekt może się skompilować poprawnie, ale mogą w dalszym ciągu oznaczony jako nieaktualny aż do znalezienia tego pliku.

Plik (plik zasobu lub.idl/.odl pliku, na przykład zawierała instrukcję include, system projektu nie można rozpoznać.

Ponieważ system projektu nie przetwarza instrukcje preprocesora (na przykład #if), problematycznych instrukcji może nie być naprawdę częścią kompilacji.

Aby rozwiązać to ostrzeżenie, Usuń wszystkie zbędny kod w plikach .rc, lub Dodaj pliki zastępcze z odpowiednią nazwę.