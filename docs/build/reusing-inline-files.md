---
title: Ponowne użycie plików wbudowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37544db8076d40e638b6ddf6f340070298229149
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722465"
---
# <a name="reusing-inline-files"></a>Ponowne użycie plików wbudowanych

Aby ponownie użyć pliku wbudowanego, należy określić <<*filename* w przypadku, gdy plik jest zdefiniowana i pierwszego, korzystać z nich *filename* bez << później w tym samym lub innym polecenia. Polecenie, aby utworzyć pliku wbudowanego musi zostać uruchomiony przed wszystkie polecenia, używające tego pliku.

## <a name="see-also"></a>Zobacz też

[Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)