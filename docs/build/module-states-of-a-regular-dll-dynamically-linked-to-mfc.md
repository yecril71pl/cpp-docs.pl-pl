---
title: Stany modułu zwykłej biblioteki DLL MFC połączonej dynamicznie z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220584"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stany modułu zwykłej biblioteki DLL MFC połączonej dynamicznie z MFC

Możliwość dynamicznego łączenia zwykłej biblioteki MFC DLL z biblioteką MFC DLL umożliwia nieskomplikowaną konfigurację. Na przykład zwykła Biblioteka MFC DLL i plik wykonywalny, który używa tego elementu, można dynamicznie łączyć się z biblioteką DLL MFC i wszystkimi bibliotekami DLL rozszerzenia MFC.

Ta konfiguracja stanowi problem w odniesieniu do danych globalnych MFC, takich jak wskaźnik do bieżącego `CWinApp` obiektu i map uchwytów.

Przed MFC w wersji 4,0, te dane globalne znajdowały się w bibliotece MFC DLL i zostały udostępnione przez wszystkie moduły w procesie. Ze względu na to, że każdy proces korzystający z biblioteki Win32 DLL pobiera własną kopię danych biblioteki DLL, ten schemat zapewnia łatwy sposób śledzenia danych dla poszczególnych procesów. Ponadto, ponieważ model AFXDLL założono, że może istnieć tylko jeden `CWinApp` obiekt i tylko jeden zestaw map uchwytów w procesie, te elementy mogą być śledzone w bibliotece MFC DLL.

Ale z możliwością dynamicznego łączenia zwykłej biblioteki MFC DLL z biblioteką MFC DLL, można teraz mieć co `CWinApp` najmniej dwa obiekty w procesie — a także co najmniej dwa zestawy uchwytów. Jak usługa MFC śledzi, które z nich powinny być używane?

Rozwiązaniem jest przyznanie każdemu modułowi (aplikacji lub zwykłej MFC DLL) własnej kopii informacji o stanie globalnym. W rezultacie wywołanie **AfxGetApp** w zwykłej bibliotece MFC DLL zwraca wskaźnik do `CWinApp` obiektu w bibliotece DLL, a nie w pliku wykonywalnym. Ta kopia dla danego modułu danych globalnych MFC jest znana jako stan modułu i jest opisana w temacie [MFC Tech uwagi 58](../mfc/tn058-mfc-module-state-implementation.md).

Procedura wspólnego okna MFC automatycznie przełącza się do prawidłowego stanu modułu, dlatego nie trzeba martwić się o niego w żadnej obsługi komunikatów wdrożonej w zwykłej bibliotece DLL MFC. Ale gdy plik wykonywalny wywołuje zwykłe biblioteki MFC DLL, należy jawnie ustawić bieżący stan modułu dla biblioteki DLL. Aby to zrobić, użyj makra **AFX_MANAGE_STATE** w każdej funkcji wyeksportowanej z biblioteki DLL. W tym celu należy dodać następujący wiersz kodu do początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
