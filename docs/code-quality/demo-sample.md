---
title: Przykładowy projekt C++ do analizy kodu
description: Jak utworzyć przykładowe rozwiązanie do użycia w instruktażu analizy kodu dla programu Microsoft C++ w programie Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372058"
---
# <a name="sample-c-project-for-code-analysis"></a>Przykładowy projekt C++ do analizy kodu

Poniższe procedury pokazują, jak utworzyć przykład dla [Instruktażu: Analizowanie kodu C/C++ pod kątem wad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Procedury tworzą:

- Rozwiązanie programu Visual Studio o nazwie *CppDemo*.

- Projekt biblioteki statycznej o nazwie *CodeDefects*.

- Statyczny projekt biblioteki o nazwie *Adnotacje*.

Procedury zawierają również kod dla nagłówka i plików *cpp* dla bibliotek statycznych.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Tworzenie rozwiązania CppDemo i projektu CodeDefects

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt**

1. W oknie **dialogowym Tworzenie nowego projektu** zmień filtr języka na **C++**.

1. Wybierz **Pozycję Kreator pulpitu systemu Windows** i wybierz przycisk **Dalej.**

1. Na stronie **Konfigurowanie nowego projektu** w polu tekstowym **Nazwa projektu** wprowadź pozycję *CodeDefects*.

1. W polu **tekstowym Nazwa rozwiązania** wprowadź *CppDemo*.

1. Wybierz pozycję **Utwórz**.

1. W oknie dialogowym **Projekt pulpitu systemu Windows** zmień typ **aplikacji** na **Biblioteka statyczna (lib).**

1. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**.

1. Wybierz **przycisk OK,** aby utworzyć rozwiązanie i projekt.

::: moniker-end

::: moniker range="vs-2017"

1. Otwórz program Visual Studio. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C++** > **Windows Desktop**.

1. Wybierz **Kreatora pulpitu systemu Windows**.

1. W polu **tekstowym Nazwa** wprowadź *pozycję CodeDefects*.

1. W polu **tekstowym Nazwa rozwiązania** wprowadź *CppDemo*.

1. Wybierz pozycję **OK**.

1. W oknie dialogowym **Projekt pulpitu systemu Windows** zmień typ **aplikacji** na **Biblioteka statyczna (lib).**

1. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**.

1. Wybierz **przycisk OK,** aby utworzyć rozwiązanie i projekt.

::: moniker-end

::: moniker range="vs-2015"

1. Otwórz program Visual Studio. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Szablony** > **visual c++** > **Win32**.

1. Wybierz **aplikację konsoli Win32**.

1. W polu **tekstowym Nazwa** wprowadź *pozycję CodeDefects*.

1. W polu **tekstowym Nazwa rozwiązania** wprowadź *CppDemo*.

1. Wybierz pozycję **OK**.

1. W oknie dialogowym **Kreator aplikacji Win32** wybierz przycisk **Dalej.**

1. Zmień **typ aplikacji** na **Biblioteka statyczna**.

1. W obszarze **Opcje dodatkowe**usuń zaznaczenie **wstępnie skompilowanego nagłówka**.

1. Wybierz **pozycję Zakończ,** aby utworzyć rozwiązanie i projekt.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Dodawanie pliku nagłówka i pliku źródłowego do projektu CodeDefects

1. W Eksploratorze rozwiązań rozwiń **pozycję CodeDefects**.

1. Kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe **dla plików nagłówkowych**. Wybierz **pozycję Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Kod programu Visual C++,** > **Code**a następnie wybierz pozycję **Plik nagłówka (h)**.

1. W polu Edycja **nazwy** wprowadź *plik Bug.h*, a następnie wybierz przycisk **Dodaj.**

1. W oknie edycji *dla Bug.h*wybierz i usuń zawartość.

1. Skopiuj poniższy kod i wklej go do pliku *Bug.h* w edytorze.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe **dla plików źródłowych**. Wybierz **pozycję Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik języka **C++ (cpp)**.

1. W polu Edycja **nazwy** wprowadź pole *Bug.cpp*, a następnie wybierz przycisk **Dodaj.**

1. Skopiuj poniższy kod i wklej go do pliku *Bug.cpp* w edytorze.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. Na pasku menu wybierz pozycję Zapisz**wszystko** **.** > 

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Dodawanie projektu Adnotacje i konfigurowanie go jako biblioteki statycznej

::: moniker range=">=vs-2019"

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **polecenie CppDemo,** aby otworzyć menu kontekstowe. Wybierz **pozycję Dodaj** > **nowy projekt**.

1. W oknie **dialogowym Dodawanie nowego projektu** wybierz pozycję **Kreator pulpitu systemu Windows**, a następnie wybierz przycisk **Dalej.**

1. Na stronie **Konfigurowanie nowego projektu** w polu tekstowym **Nazwa projektu** wprowadź pozycję *Adnotacje*, a następnie wybierz pozycję **Utwórz**.

1. W oknie dialogowym **Projekt pulpitu systemu Windows** zmień typ **aplikacji** na **Biblioteka statyczna (lib).**

1. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**.

1. Wybierz **przycisk OK,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **polecenie CppDemo,** aby otworzyć menu kontekstowe. Wybierz **pozycję Dodaj** > **nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję Visual **C++** > **Windows Desktop**.

1. Wybierz **Kreatora pulpitu systemu Windows**.

1. W polu **tekstowym Nazwa** wprowadź pozycję *Adnotacje*, a następnie wybierz przycisk **OK**.

1. W oknie dialogowym **Projekt pulpitu systemu Windows** zmień typ **aplikacji** na **Biblioteka statyczna (lib).**

1. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**.

1. Wybierz **przycisk OK,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **polecenie CppDemo,** aby otworzyć menu kontekstowe. Wybierz **pozycję Dodaj** > **nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję Visual **C++** > **Win32**.

1. Wybierz **aplikację konsoli Win32**.

1. W polu **tekstowym Nazwa** wprowadź *adnotacje*.

1. Wybierz pozycję **OK**.

1. W oknie dialogowym **Kreator aplikacji Win32** wybierz przycisk **Dalej.**

1. Zmień **typ aplikacji** na **Biblioteka statyczna**.

1. W obszarze **Opcje dodatkowe**usuń zaznaczenie **wstępnie skompilowanego nagłówka**.

1. Wybierz **pozycję Zakończ,** aby utworzyć projekt.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Dodawanie pliku nagłówka i pliku źródłowego do projektu Adnotacje

1. W Eksploratorze rozwiązań rozwiń **węzeł Adnotacje**.

1. Kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe **dla plików nagłówków** w obszarze **Adnotacje**. Wybierz **pozycję Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Kod programu Visual C++,** > **Code**a następnie wybierz pozycję **Plik nagłówka (h)**.

1. W polu Edycja **nazwy** wprowadź *plik adnotations.h*, a następnie wybierz przycisk **Dodaj.**

1. W oknie edycji *adnotations.h*zaznacz i usuń zawartość.

1. Skopiuj poniższy kod i wklej go do pliku *adnotations.h* w edytorze.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe **dla plików źródłowych** w obszarze **Adnotacje**. Wybierz **pozycję Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik języka **C++ (cpp)**.

1. W polu Edycja **nazwy** wprowadź *polecenie adnotations.cpp*, a następnie wybierz przycisk **Dodaj.**

1. Skopiuj poniższy kod i wklej go do pliku *adnotations.cpp* w edytorze.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. Na pasku menu wybierz pozycję Zapisz**wszystko** **.** > 

Rozwiązanie zostało ukończone i powinno zostać skompilowe bez błędów.

::: moniker range="vs-2017"

> [!NOTE]
> W programie Visual Studio 2017 może `E1097 unknown attribute "no_init_all"` pojawić się fałszywe ostrzeżenie w silniku IntelliSense. Możesz bezpiecznie zignorować to ostrzeżenie.

::: moniker-end
