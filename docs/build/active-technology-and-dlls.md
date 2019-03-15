---
title: Technologia Active i biblioteki DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: 9633d60520a2a634ffe78d0fb9d48f6dd2ca7333
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817455"
---
# <a name="active-technology-and-dlls"></a>Technologia Active i biblioteki DLL

Technologia Active umożliwia serwerów obiektów wewnątrz biblioteki DLL całkowite wdrożenie. Ten typ serwera jest nazywany serwerem w procesie. MFC nie całkowicie obsługuje serwery wewnątrzprocesowe dla wszystkich funkcji edycja wizualna przede wszystkim, ponieważ technologia Active nie zapewnia sposób, aby serwer mógł dołączyć do kontenera główna pętla wiadomości. MFC wymaga dostępu do aplikacji kontenera pętli komunikatów do obsługi klawiszy i przetwarzanie w czasie bezczynności (%).

Jeśli piszesz serwera automatyzacji, a serwer nie ma interfejsu użytkownika, można utworzyć serwera wewnątrz procesowego i umieść je całkowicie biblioteki DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Serwery automatyzacji](../mfc/automation-servers.md)

## <a name="see-also"></a>Zobacz także

[Biblioteki DLL w programie Visual C++](dlls-in-visual-cpp.md)
