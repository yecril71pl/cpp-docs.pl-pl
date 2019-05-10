---
title: Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC
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
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC

Możliwość dynamicznego połączyć zwykłej biblioteki MFC DLL biblioteki MFC DLL umożliwia pewne konfiguracje, które są bardzo skomplikowane. Na przykład zwykłej biblioteki MFC DLL i plik wykonywalny, który korzysta z niego można zarówno dynamiczne łącze do biblioteki MFC DLL i wszystkie biblioteki DLL rozszerzeń MFC.

Konfiguracja ta stanowi problem w odniesieniu do danych globalnych MFC, takich jak wskaźnik do bieżącego `CWinApp` obiektu i obsługują mapy.

Przed MFC w wersji 4.0 to dane globalne znajdowały się w bibliotece DLL MFC, się i został udostępniony przez wszystkie moduły w procesie. Ponieważ każdy proces, korzystając z biblioteki DLL systemu Win32 pobiera własną kopię danych biblioteki DLL, ten schemat zapewnić łatwy sposób śledzenia na przetwarzanie danych. Ponadto ponieważ AFXDLL model założyć, że będzie istnieć tylko jeden `CWinApp` obiektu i tylko jeden zestaw obsługi map w procesie, te elementy można śledzić w biblioteki MFC DLL, sam.

Ale z możliwością połączyć dynamicznie zwykłej biblioteki MFC DLL biblioteki MFC DLL, obecnie istnieje możliwość mają co najmniej dwóch `CWinApp` obiektów w procesie — i również dwa lub więcej zestawów dojście do mapy. Jak MFC zachować informacje o te, które powinien używać?

Rozwiązaniem jest zapewnienie własną kopię tych informacji globalny stan każdego modułu (aplikacji lub zwykłej biblioteki MFC DLL). W związku z tym, wywołanie **afxgetapp —** w zwykłej biblioteki MFC DLL zwraca wskaźnik do `CWinApp` obiektu w bibliotece DLL, nie jeden w pliku wykonywalnym. -Module kopii danych globalnych MFC jest znany jako stanu modułu i jest opisany w [58 Uwaga techniczna MFC](../mfc/tn058-mfc-module-state-implementation.md).

MFC wspólnej procedury okna przełącza się do stanu do modułu, dzięki czemu nie trzeba już martwić się o go w dowolnej procedury obsługi komunikatów w zwykłej biblioteki MFC DLL. Jednak gdy plik wykonywalny wywołuje do zwykłej biblioteki MFC DLL, trzeba jawnie ustawione bieżący stan modułu dla biblioteki DLL. Aby to zrobić, należy użyć **AFX_MANAGE_STATE** makra w każdej funkcji wyeksportowane z biblioteki DLL. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
