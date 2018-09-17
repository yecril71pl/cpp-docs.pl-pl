---
title: Technologia Active i biblioteki dll | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efa9a5cf17a4578fc7be9cbadc51605ee32c1650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706254"
---
# <a name="active-technology-and-dlls"></a>Technologia Active i biblioteki DLL

Technologia Active umożliwia serwerów obiektów wewnątrz biblioteki DLL całkowite wdrożenie. Ten typ serwera jest nazywany serwerem w procesie. MFC nie całkowicie obsługuje serwery wewnątrzprocesowe dla wszystkich funkcji edycja wizualna przede wszystkim, ponieważ technologia Active nie zapewnia sposób, aby serwer mógł dołączyć do kontenera główna pętla wiadomości. MFC wymaga dostępu do aplikacji kontenera pętli komunikatów do obsługi klawiszy i przetwarzanie w czasie bezczynności (%).

Jeśli piszesz serwera automatyzacji, a serwer nie ma interfejsu użytkownika, można utworzyć serwera wewnątrz procesowego i umieść je całkowicie biblioteki DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Serwery automatyzacji](../mfc/automation-servers.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)