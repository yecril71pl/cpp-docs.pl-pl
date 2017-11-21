---
title: Klasa CPathT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
dev_langs: C++
helpviewer_keywords: CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9abb6a20beca39e8224ab3d3724da9664f68702
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cpatht-class"></a>Klasa CPathT
Ta klasa reprezentuje ścieżkę.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>Parametry  
 `StringType`  
 ATL/MFC klasy ciągu dla ścieżki (zobacz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|Typ stałej ciągu.|  
|[CPathT::PXSTR](#pxstr)|Typ ciągu.|  
|[CPathT::XCHAR](#xchar)|Typ znaków.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|Konstruktor dla ścieżki.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|Wywołaj tę metodę, aby dodać ukośnikiem na końcu ciągu do utworzenia prawidłowa składnia ścieżki.|  
|[CPathT::AddExtension](#addextension)|Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.|  
|[CPathT::Append](#append)|Wywołanie tej metody, aby dołączyć ciąg do bieżącej ścieżki.|  
|[CPathT::BuildRoot](#buildroot)|Wywołanie tej metody można utworzyć ścieżki katalogu głównego z liczbą danego dysku.|  
|[CPathT::Canonicalize](#canonicalize)|Wywołanie tej metody można przekonwertować ścieżki do postaci kanonicznej.|  
|[CPathT::Combine](#combine)|Wywołanie tej metody do łączenia ciąg reprezentujący nazwę katalogu, a ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżki.|  
|[CPathT::CommonPrefix](#commonprefix)|Wywołaj tę metodę, aby określić, czy podana ścieżka udostępnia typowe prefiks bieżącej ścieżki.|  
|[CPathT::CompactPath](#compactpath)|Wywołać tę metodę do obcięcia mieścić się w szerokości pikselu przez zamianę składników ścieżki wielokropek ścieżki pliku.|  
|[CPathT::CompactPathEx](#compactpathex)|Wywołać tę metodę do obcięcia mieścić się w podanej liczbie znaków przez zamianę składników ścieżki wielokropek ścieżki pliku.|  
|[CPathT::FileExists](#fileexists)|Wywołanie tej metody, aby sprawdzić, czy istnieje plik o tej nazwy ścieżki.|  
|[CPathT::FindExtension](#findextension)|Wywołanie tej metody, aby znaleźć pozycję rozszerzenie pliku w ścieżce.|  
|[CPathT::FindFileName](#findfilename)|Wywołaj tę metodę, aby znaleźć nazwę pliku w ścieżce.|  
|[CPathT::GetDriveNumber](#getdrivenumber)|Wywołaj tę metodę, aby wyszukać ścieżkę na literę dysku do zakresu od "A" do "Z" i zwracać jej numer dysku.|  
|[CPathT::GetExtension](#getextension)|Wywołaj tę metodę w celu pobrania rozszerzenie pliku ze ścieżki.|  
|[CPathT::IsDirectory](#isdirectory)|Wywołanie tej metody, aby sprawdzić, czy ścieżka jest prawidłowym katalogiem.|  
|[CPathT::IsFileSpec](#isfilespec)|Wywołanie tej metody do ścieżki dla znaków oddzielającego ścieżki wyszukiwania (na przykład ":" lub "\\"). Jeśli nie są oddzielającego ścieżki znaki obecne, ścieżka uważa się ścieżka Specyfikacja pliku.|  
|[CPathT::IsPrefix](#isprefix)|Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks przekazany typ `pszPrefix`.|  
|[CPathT::IsRelative](#isrelative)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest względna.|  
|[CPathT::IsRoot](#isroot)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest głównego katalogu.|  
|[CPathT::IsSameRoot](#issameroot)|Wywołaj tę metodę, aby określić, czy składnik główny wspólnego z bieżącej ścieżki inną ścieżkę.|  
|[CPathT::IsUNC](#isunc)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal konwencją nazewnictwa) dla serwera i udziału.|  
|[CPathT::IsUNCServer](#isuncserver)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal konwencją nazewnictwa) dla tylko serwer.|  
|[CPathT::IsUNCServerShare](#isuncservershare)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę udziału UNC (universal konwencją nazewnictwa) \\ \  *serwera*\ *udostępnianie*.|  
|[CPathT::MakePretty](#makepretty)|Wywołanie tej metody można przekonwertować ścieżki na wszystkie małe litery, aby zapewnić spójny wygląd ścieżki.|  
|[CPathT::MatchSpec](#matchspec)|Wywołaj tę metodę, aby wyszukać ścieżkę na ciąg zawierający typ dopasowania symboli wieloznacznych.|  
|[CPathT::QuoteSpaces](#quotespaces)|Wywołanie tej metody zawiera spacje, ujmij ścieżkę w znaki cudzysłowu.|  
|[CPathT::RelativePathTo](#relativepathto)|Wywołanie tej metody, aby utworzyć ścieżki względnej z jednego pliku lub folderu.|  
|[CPathT::RemoveArgs](#removeargs)|Wywołaj tę metodę w celu usunięcia żadnych argumentów wiersza polecenia ze ścieżki.|  
|[CPathT::RemoveBackslash](#removebackslash)|Wywołaj tę metodę, aby usunąć ukośnik odwrotny na końcu ze ścieżki.|  
|[CPathT::RemoveBlanks](#removeblanks)|Wywołaj tę metodę w celu usunięcia wszystkich spacji wiodących i końcowych z ścieżki.|  
|[CPathT::RemoveExtension](#removeextension)|Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.|  
|[CPathT::RemoveFileSpec](#removefilespec)|Wywołać tę metodę, aby usunąć końcu nazwy pliku i ukośnika odwrotnego ze ścieżki, jeśli ma ona je.|  
|[CPathT::RenameExtension](#renameextension)|Wywołanie tej metody, aby zastąpić nowego rozszerzenia rozszerzenie nazwy pliku w ścieżce. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączona do końca ciągu.|  
|[CPathT::SkipRoot](#skiproot)|Wywołanie tej metody można przeanalizować ścieżki, ignorowanie litery dysku lub części ścieżki UNC serwera i udostępniania.|  
|[CPathT::StripPath](#strippath)|Wywołaj tę metodę w celu usunięcia części ścieżki w pełni kwalifikowaną ścieżkę i nazwę pliku.|  
|[CPathT::StripToRoot](#striptoroot)|Wywołaj tę metodę, aby usunąć wszystkie części ścieżki z wyjątkiem informacji katalogu głównego.|  
|[CPathT::UnquoteSpaces](#unquotespaces)|Wywołaj tę metodę, aby usunąć znaki cudzysłowu na początku i końca ścieżki.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Ten operator sprawia, że obiekt traktowane jak ciąg.|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Ten operator sprawia, że obiekt traktowane jak ciąg.|  
|[CPathT::operator StringType &](#operator_stringtype)|Ten operator sprawia, że obiekt traktowane jak ciąg.|  
|[CPathT::operator +=](#operator_add_eq)|Ten operator dołącza ciąg do ścieżki.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|Ścieżka.|  
  
## <a name="remarks"></a>Uwagi  
 `CPath`, `CPathA`, i `CPathW` są wystąpieniami `CPathT` zdefiniowane w następujący sposób:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlpath.h  
  
##  <a name="addbackslash"></a>CPathT::AddBackslash  
 Wywołaj tę metodę, aby dodać ukośnikiem na końcu ciągu do utworzenia prawidłowa składnia ścieżki. Jeśli ścieżka zawiera już końcowy ukośnik odwrotny, brak ukośnika zostaną dodane.  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
##  <a name="addextension"></a>CPathT::AddExtension  
 Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parametry  
 `pszExtension`  
 Rozszerzenie pliku do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
##  <a name="append"></a>CPathT::Append  
 Wywołanie tej metody, aby dołączyć ciąg do bieżącej ścieżki.  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parametry  
 `pszMore`  
 Ciąg do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
##  <a name="buildroot"></a>CPathT::BuildRoot  
 Wywołanie tej metody można utworzyć ścieżki katalogu głównego z liczbą danego dysku.  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>Parametry  
 *iDrive*  
 Numeru dysku (A: to 0, 1 B: itd.).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
##  <a name="canonicalize"></a>CPathT::Canonicalize  
 Wywołanie tej metody można przekonwertować ścieżki do postaci kanonicznej.  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
##  <a name="combine"></a>CPathT::Combine  
 Wywołanie tej metody do łączenia ciąg reprezentujący nazwę katalogu, a ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżki.  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>Parametry  
 `pszDir`  
 Ścieżka katalogu.  
  
 *pszFile*  
 Ścieżka do pliku.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).  
  
##  <a name="commonprefix"></a>CPathT::CommonPrefix  
 Wywołaj tę metodę, aby określić, czy podana ścieżka udostępnia typowe prefiks bieżącej ścieżki.  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>Parametry  
 `pszOther`  
 Ścieżka do porównania z bieżącym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca Wspólny prefiks.  
  
### <a name="remarks"></a>Uwagi  
 Prefiks jest jednym z następujących typów: "C:\\\\",".","..",".. \\\\". Aby uzyskać więcej informacji, zobacz [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
##  <a name="compactpath"></a>CPathT::CompactPath  
 Wywołać tę metodę do obcięcia mieścić się w szerokości pikselu przez zamianę składników ścieżki wielokropek ścieżki pliku.  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `hDC`  
 Kontekst urządzenia używane do mierniki czcionki.  
  
 `nWidth`  
 Szerokość w pikselach, które zostanie wymuszone ciąg mieści się w.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
##  <a name="compactpathex"></a>CPathT::CompactPathEx  
 Wywołać tę metodę do obcięcia mieścić się w podanej liczbie znaków przez zamianę składników ścieżki wielokropek ścieżki pliku.  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxChars`  
 Maksymalna liczba znaków, które mają zostać zawarte w nowe parametry, łącznie z znak końcowy NULL.  
  
 `dwFlags`  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
##  <a name="cpatht"></a>CPathT::CPathT  
 Konstruktor.  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pszPath*  
 Wskaźnik do ciągu ścieżki.  
  
 *Ścieżka*  
 Ciąg ścieżki.  
  
##  <a name="fileexists"></a>CPathT::FileExists  
 Wywołanie tej metody, aby sprawdzić, czy istnieje plik o tej nazwy ścieżki.  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli plik istnieje, wartość FALSE w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
##  <a name="findextension"></a>CPathT::FindExtension  
 Wywołanie tej metody, aby znaleźć pozycję rozszerzenie pliku w ścieżce.  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycję "." poprzedzających rozszerzenia. Jeśli rozszerzenie nie zostanie znaleziony, zwraca -1.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
##  <a name="findfilename"></a>CPathT::FindFileName  
 Wywołaj tę metodę, aby znaleźć nazwę pliku w ścieżce.  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę pliku. Jeśli żadna nazwa pliku zostanie znaleziony, zwraca -1.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber  
 Wywołaj tę metodę, aby wyszukać ścieżkę na literę dysku do zakresu od "A" do "Z" i zwracać jej numer dysku.  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca numer dysku jako liczba całkowita z przedziału od 0 do 25 (odpowiadający "A" do "Z") Jeśli ścieżka zawiera literę dysku lub -1, w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
##  <a name="getextension"></a>CPathT::GetExtension  
 Wywołaj tę metodę w celu pobrania rozszerzenie pliku ze ścieżki.  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozszerzenie pliku.  
  
##  <a name="isdirectory"></a>CPathT::IsDirectory  
 Wywołanie tej metody, aby sprawdzić, czy ścieżka jest prawidłowym katalogiem.  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość inną niż zero (16), jeśli ścieżka jest katalogiem, `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).  
  
##  <a name="isfilespec"></a>CPathT::IsFileSpec  
 Wywołanie tej metody do ścieżki dla znaków oddzielającego ścieżki wyszukiwania (na przykład ":" lub "\\"). Jeśli nie są oddzielającego ścieżki znaki obecne, ścieżka uważa się ścieżka Specyfikacja pliku.  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli nie są oddzielającego ścieżki znaki w ścieżce, lub FAŁSZ, jeśli występują znaki oddzielającego ścieżki.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
##  <a name="isprefix"></a>CPathT::IsPrefix  
 Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks przekazany typ `pszPrefix`.  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrefix`  
 Prefiks do wyszukania. Prefiks jest jednym z następujących typów: "C:\\\\",".","..",".. \\\\".  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli ścieżka zawiera prefiks, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
##  <a name="isrelative"></a>CPathT::IsRelative  
 Wywołaj tę metodę w celu ustalenia, czy ścieżka jest względna.  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli ścieżka jest względna, lub FAŁSZ, gdy jest bezwzględny.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
##  <a name="isroot"></a>CPathT::IsRoot  
 Wywołaj tę metodę w celu ustalenia, czy ścieżka jest głównego katalogu.  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli ścieżka jest katalogu głównego, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
##  <a name="issameroot"></a>CPathT::IsSameRoot  
 Wywołaj tę metodę, aby określić, czy składnik główny wspólnego z bieżącej ścieżki inną ścieżkę.  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszOther`  
 Innej ścieżki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli oba parametry mają tego samego składnika głównego, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
##  <a name="isunc"></a>CPathT::IsUNC  
 Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal konwencją nazewnictwa) dla serwera i udziału.  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli ścieżka jest prawidłowa ścieżka UNC, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
##  <a name="isuncserver"></a>CPathT::IsUNCServer  
 Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal konwencją nazewnictwa) dla tylko serwer.  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli ciąg jest prawidłową ścieżką UNC serwera tylko (Brak nazwy udziału), lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare  
 Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę udziału UNC (universal konwencją nazewnictwa) \\ \  *serwera*\ *udostępnianie*.  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli ścieżka znajduje się w formularzu \\ \  *serwera*\ *udostępnianie*, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
##  <a name="m_strpath"></a>CPathT::m_strPath  
 Ścieżka.  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>Uwagi  
 `StringType`jest to parametr szablonu do `CPathT`.  
  
##  <a name="makepretty"></a>CPathT::MakePretty  
 Wywołanie tej metody można przekonwertować ścieżki na wszystkie małe litery, aby zapewnić spójny wygląd ścieżki.  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przeciwnym razie zwraca wartość TRUE, jeśli ścieżka została przekonwertowana, lub FAŁSZ.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
##  <a name="matchspec"></a>CPathT::MatchSpec  
 Wywołaj tę metodę, aby wyszukać ścieżkę na ciąg zawierający typ dopasowania symboli wieloznacznych.  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszSpec`  
 Wskaźnik do zerem ciągu z typem plików do wyszukania. Na przykład, aby sprawdzić, czy plik w bieżącej ścieżce jest plikiem DOC `pszSpec` powinna być równa "* doc".  
  
### <a name="return-value"></a>Wartość zwracana  
 W przeciwnym razie zwraca wartość TRUE, jeśli ciąg jest zgodny, lub FAŁSZ.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
##  <a name="operator_add_eq"></a>CPathT::operator +=  
 Ten operator dołącza ciąg do ścieżki.  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parametry  
 `pszMore`  
 Ciąg do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ścieżkę zaktualizowane.  
  
##  <a name="operator_const_stringtype_amp"></a>CPathT::operator const StringType&amp;  
 Ten operator sprawia, że obiekt traktowane jak ciąg.  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg reprezentujący bieżącej ścieżki, które są zarządzane przez ten obiekt.  
  
##  <a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR  
 Ten operator sprawia, że obiekt traktowane jak ciąg.  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg reprezentujący bieżącej ścieżki, które są zarządzane przez ten obiekt.  
  
##  <a name="operator_stringtype__amp"></a>CPathT::operator StringType&amp;  
 Ten operator sprawia, że obiekt traktowane jak ciąg.  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg reprezentujący bieżącej ścieżki, które są zarządzane przez ten obiekt.  
  
##  <a name="pcxstr"></a>CPathT::PCXSTR  
 Typ stałej ciągu.  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>Uwagi  
 `StringType`jest to parametr szablonu do `CPathT`.  
  
##  <a name="pxstr"></a>CPathT::PXSTR  
 Typ ciągu.  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>Uwagi  
 `StringType`jest to parametr szablonu do `CPathT`.  
  
##  <a name="quotespaces"></a>CPathT::QuoteSpaces  
 Wywołanie tej metody zawiera spacje, ujmij ścieżkę w znaki cudzysłowu.  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
##  <a name="relativepathto"></a>CPathT::RelativePathTo  
 Wywołanie tej metody, aby utworzyć ścieżki względnej z jednego pliku lub folderu.  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFrom`  
 Początek ścieżki względnej.  
  
 *dwAttrFrom*  
 Atrybuty pliku `pszFrom`. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, `pszFrom` zakładanego katalogiem, a w przeciwnym razie `pszFrom` zakłada, że plik.  
  
 `pszTo`  
 Punkt końcowy ścieżki względnej.  
  
 *dwAttrTo*  
 Atrybuty pliku `pszTo`. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, `pszTo` zakładanego katalogiem, a w przeciwnym razie `pszTo` zakłada, że plik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
##  <a name="removeargs"></a>CPathT::RemoveArgs  
 Wywołaj tę metodę w celu usunięcia żadnych argumentów wiersza polecenia ze ścieżki.  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
##  <a name="removebackslash"></a>CPathT::RemoveBackslash  
 Wywołaj tę metodę, aby usunąć ukośnik odwrotny na końcu ze ścieżki.  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
##  <a name="removeblanks"></a>CPathT::RemoveBlanks  
 Wywołaj tę metodę w celu usunięcia wszystkich spacji wiodących i końcowych z ścieżki.  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
##  <a name="removeextension"></a>CPathT::RemoveExtension  
 Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
##  <a name="removefilespec"></a>CPathT::RemoveFileSpec  
 Wywołać tę metodę, aby usunąć końcu nazwy pliku i ukośnika odwrotnego ze ścieżki, jeśli ma ona je.  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
##  <a name="renameextension"></a>CPathT::RenameExtension  
 Wywołanie tej metody, aby zastąpić nowego rozszerzenia rozszerzenie nazwy pliku w ścieżce. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączona do końca ścieżki.  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parametry  
 `pszExtension`  
 Nowe rozszerzenie nazwy pliku poprzedzony przez "." znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
##  <a name="skiproot"></a>CPathT::SkipRoot  
 Wywołanie tej metody można przeanalizować ścieżki, ignorowanie litery dysku lub części ścieżki UNC (universal konwencją nazewnictwa) serwera i udostępniania.  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycję początku podrzędną, poniżej katalogu głównego (literę dysku lub udziału serwera UNC).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
##  <a name="strippath"></a>CPathT::StripPath  
 Wywołaj tę metodę w celu usunięcia części ścieżki w pełni kwalifikowaną ścieżkę i nazwę pliku.  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
##  <a name="striptoroot"></a>CPathT::StripToRoot  
 Wywołaj tę metodę, aby usunąć wszystkie części ścieżki z wyjątkiem informacji katalogu głównego.  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli prawidłową literę dysku został znaleziony w ścieżce, lub FAŁSZ w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces  
 Wywołaj tę metodę, aby usunąć znaki cudzysłowu na początku i końca ścieżki.  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
##  <a name="xchar"></a>CPathT::XCHAR  
 Typ znaków.  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>Uwagi  
 `StringType`jest to parametr szablonu do `CPathT`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)   
 [Klasa CStringT](../../atl-mfc-shared/reference/cstringt-class.md)