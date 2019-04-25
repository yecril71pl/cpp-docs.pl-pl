---
title: Ostrzeżenie PRJ0041 dotyczące kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297726"
---
# <a name="project-build-warning-prj0041"></a>Ostrzeżenie PRJ0041 dotyczące kompilacji projektu

Nie można odnaleźć brakującej zależności 'zależności' dla pliku 'Plik'. Projekt może się skompilować poprawnie, ale mogą w dalszym ciągu oznaczony jako nieaktualny aż do znalezienia tego pliku.

Plik (plik zasobu lub.idl/.odl pliku, na przykład zawierała instrukcję include, system projektu nie można rozpoznać.

Ponieważ system projektu nie przetwarza instrukcje preprocesora (na przykład #if), problematycznych instrukcji może nie być naprawdę częścią kompilacji.

Aby rozwiązać to ostrzeżenie, Usuń wszystkie zbędny kod w plikach .rc, lub Dodaj pliki zastępcze z odpowiednią nazwę.