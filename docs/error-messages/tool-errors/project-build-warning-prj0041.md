---
title: Ostrzeżenie PRJ0041 dotyczące kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191938"
---
# <a name="project-build-warning-prj0041"></a>Ostrzeżenie PRJ0041 dotyczące kompilacji projektu

Nie można odnaleźć brakującej zależności "zależność" dla pliku "File". Projekt może być nadal kompilowany, ale może być nadal nieaktualny do momentu znalezienia tego pliku.

Plik (plik zasobów lub IDL/. ODL, na przykład zawiera instrukcję include, której system projektu nie mógł rozpoznać.

Ponieważ system projektu nie przetwarza instrukcji preprocesora (na przykład #if), instrukcja powodująca problemy może nie być częścią kompilacji.

Aby usunąć to ostrzeżenie, usuń cały niezbędny kod w plikach. RC lub Dodaj pliki zastępcze o odpowiedniej nazwie.
