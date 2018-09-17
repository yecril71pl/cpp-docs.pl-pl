---
title: Importowanie do aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- importing DLLs [C++], applications
- applications [C++], importing into
ms.assetid: 9d646466-e12e-4710-8ad9-c819c0375fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88d34ce685e22e561683cc33db25997650ed7fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718391"
---
# <a name="importing-into-an-application"></a>Importowanie do aplikacji

Funkcje można zaimportować do aplikacji przy użyciu dwóch metod:

- Używać słów kluczowych **__declspec(dllimport)** w definicji funkcji w głównym aplikacji

- Przy użyciu pliku definicji (.def) moduł wraz z **atrybutu __declspec(dllimport)**

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)](../build/importing-function-calls-using-declspec-dllimport.md)

- [Importowanie danych przy użyciu __declspec(dllimport)](../build/importing-data-using-declspec-dllimport.md)

- [Importowanie przy użyciu plików DEF](../build/importing-using-def-files.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](../build/importing-and-exporting.md)