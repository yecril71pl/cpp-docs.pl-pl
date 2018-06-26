---
title: Initinstance — funkcja członkowska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9379fef6a1d676d6a3bc757ee51d5d27acd5f6f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930179"
---
# <a name="initinstance-member-function"></a>InitInstance — Funkcja członkowska
System operacyjny Windows umożliwia uruchamianie więcej niż jedną kopię lub "instance" tej samej aplikacji. `WinMain` wywołania [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) za każdym razem uruchamia nowe wystąpienie aplikacji.  
  
 Standardowe `InitInstance` implementacji tworzone przez Kreatora aplikacji MFC wykonuje następujące zadania:  
  
-   Jako jego centralnej akcja tworzy szablonów dokumentów, które z kolei tworzenie dokumentów, widoków i okien ramowych. Opis tego procesu, zobacz [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md).  
  
-   Ładuje Opcje standardowego pliku z pliku ini lub rejestru systemu Windows, łącznie z nazwami ostatnio używanych plików.  
  
-   Rejestruje co najmniej jeden szablon dokumentu.  
  
-   Tworzy główne okno ramowe dla aplikacji MDI.  
  
-   Przetwarza wiersza polecenia, można otworzyć dokumentu, określona w wierszu polecenia lub, aby otworzyć nowy, pusty dokument.  
  
 Można dodać kodu inicjowania lub zmodyfikować kod napisany przez kreatora.  
  
> [!NOTE]
>  Aplikacje MFC musi zostać zainicjowany jako pojedynczy wątków typu apartment (STA). Jeśli należy wywołać [funkcja CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) w Twojej `InitInstance` zastępowania, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED). Aby uzyskać więcej informacji, zobacz PRB: MFC aplikacja przestaje odpowiadać podczas inicjowania aplikacji jako wielowątkowe apartamentu (828643) w [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
