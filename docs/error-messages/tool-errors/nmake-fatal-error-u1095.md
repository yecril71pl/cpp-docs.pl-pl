---
title: Błąd krytyczny NMAKE U1095
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 0ff71a229defe7a12886c1154a69bcf0432b8cca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298402"
---
# <a name="nmake-fatal-error-u1095"></a>Błąd krytyczny NMAKE U1095

rozwinięty wiersz polecenia "wiersz polecenia" zbyt długo

Po rozwinięciu makra danego wiersza polecenia przekroczyła limit długości wiersze poleceń systemu operacyjnego.

MS-DOS zezwala na maksymalnie 128 znaków, w wierszu polecenia.

W przypadku polecenia dla programu, który może akceptować wejście wiersza polecenia z pliku, zmień polecenie, a następnie podaj dane wejściowe z pliku na dysku lub pliku wbudowanego. Na przykład łącze i LIB akceptuje dane wejściowe z pliku odpowiedzi.