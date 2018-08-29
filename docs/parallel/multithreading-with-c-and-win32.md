---
title: Wielowątkowość z C i podsystemem Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444421a099fac7635dd668c12b22600d33d60f8b
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130756"
---
# <a name="multithreading-with-c-and-win32"></a>Wielowątkowość z językiem C i podsystemem Win32
Microsoft Visual C++ zapewnia obsługę tworzenia aplikacji wielowątkowych. Należy rozważyć użycie więcej niż jeden wątek, jeśli Twoja aplikacja potrzebuje do wykonywania kosztownych operacji, które mogą być przyczyną interfejsu użytkownika przestanie odpowiadać.  
  
Za pomocą języka Visual C++, istnieją dwa sposoby programowania z wieloma wątkami: za pomocą biblioteki Microsoft Foundation Class (MFC) lub biblioteki wykonawczej C i Win32 API. Aby uzyskać informacje o tworzeniu aplikacji wielowątkowych w MFC, zobacz [wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md) po przeczytaniu następujących tematów dotyczących wielowątkowości w C.  
  
Te tematy tłumaczą funkcje Visual C++, które obsługują tworzenie programów wielowątkowych.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
- [Co wielowątkowość dotyczy](multithread-programs.md)  
  
- [Obsługa bibliotek dla wielowątkowości](library-support-for-multithreading.md)  
  
- [Uwzględnianie plików na potrzeby wielowątkowości](include-files-for-multithreading.md)  
  
- [Funkcje biblioteki uruchomieniowej C do sterowania wątkami](c-run-time-library-functions-for-thread-control.md)  
  
- [Przykładowy program wielowątkowy w języku C](sample-multithread-c-program.md)  
  
- [Pisanie wielowątkowego programu Win32](writing-a-multithreaded-win32-program.md)  
  
- [Kompilowanie i łączenie programów wielowątkowych](compiling-and-linking-multithread-programs.md)  
  
- [Unikanie obszarów problemów z programami wielowątkowymi](avoiding-problem-areas-with-multithread-programs.md)  
  
- [Lokalny magazyn wątków (TLS)](thread-local-storage-tls.md)  
  
## <a name="see-also"></a>Zobacz też  
 
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)