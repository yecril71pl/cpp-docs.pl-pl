---
title: Funkcje ścieżki ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d5b3677ab256e6d1b3e88f5bc71c8b9c7b097b2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753295"
---
# <a name="atl-path-functions"></a>Funkcje ścieżki ATL

ATL udostępnia klasę ATLPath do manipulowania ścieżek w formie [CPathT](cpatht-class.md). Ten kod można znaleźć w atlpath.h.

### <a name="related-classes"></a>Klasy pokrewne

|||
|-|-|
|[Klasa CPathT](cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|

### <a name="related-typedefs"></a>Powiązane definicje typów

|||
|-|-|
|`CPath`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CString`.|
|`CPathA`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringA`.|
|`CPathW`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringW`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Ta funkcja to przeciążona otoka dla [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).|
|[ATLPath::AddExtension](#addextension)|Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).|
|[ATLPath::Append](#append)|Ta funkcja to przeciążona otoka dla [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).|
|[ATLPath::BuildRoot](#buildroot)|Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).|
|[ATLPath::Canonicalize](#canonicalize)|Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).|
|[ATLPath::Combine](#combine)|Ta funkcja to przeciążona otoka dla [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).|
|[ATLPath::CommonPrefix](#commonprefix)|Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).|
|[ATLPath::CompactPath](#compactpath)|Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).|
|[ATLPath::CompactPathEx](#compactpathex)|Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).|
|[ATLPath::FileExists](#fileexists)|Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).|
|[ATLPath::FindExtension](#findextension)|Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).|
|[ATLPath::FindFileName](#findfilename)|Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).|
|[ATLPath::IsDirectory](#isdirectory)|Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).|
|[ATLPath::IsFileSpec](#isfilespec)|Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).|
|[ATLPath::IsPrefix](#isprefix)|Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).|
|[ATLPath::IsRelative](#isrelative)|Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).|
|[ATLPath::IsRoot](#isroot)|Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).|
|[ATLPath::IsSameRoot](#issameroot)|Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).|
|[ATLPath::IsUNC](#isunc)|Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).|
|[ATLPath::IsUNCServer](#isuncserver)|Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).|
|[ATLPath::MakePretty](#makepretty)|Ta funkcja to przeciążona otoka dla [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).|
|[ATLPath::MatchSpec](#matchspec)|Ta funkcja to przeciążona otoka dla [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).|
|[ATLPath::QuoteSpaces](#quotespaces)|Ta funkcja to przeciążona otoka dla [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).|
|[ATLPath::RelativePathTo](#relativepathto)|Ta funkcja to przeciążona otoka dla [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).|
|[ATLPath::RemoveArgs](#removeargs)|Ta funkcja to przeciążona otoka dla [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).|
|[ATLPath::RemoveBackslash](#removebackslash)|Ta funkcja to przeciążona otoka dla [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).|
|[ATLPath::RemoveBlanks](#removeblanks)|Ta funkcja to przeciążona otoka dla [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).|
|[ATLPath::RemoveExtension](#removeextension)|Ta funkcja to przeciążona otoka dla [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Ta funkcja to przeciążona otoka dla [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).|
|[ATLPath::RenameExtension](#renameextension)|Ta funkcja to przeciążona otoka dla [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).|
|[ATLPath::SkipRoot](#skiproot)|Ta funkcja to przeciążona otoka dla [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).|
|[ATLPath::StripPath](#strippath)|Ta funkcja to przeciążona otoka dla [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).|
|[ATLPath::StripToRoot](#striptoroot)|Ta funkcja to przeciążona otoka dla [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Ta funkcja to przeciążona otoka dla [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Ta funkcja to przeciążona otoka dla [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

### <a name="syntax"></a>Składnia

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha) Aby uzyskać szczegółowe informacje.

## <a name="addextension"></a> ATLPath::AddExtension

Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

### <a name="syntax"></a>Składnia

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona) Aby uzyskać szczegółowe informacje.

## <a name="append"></a> ATLPath::Append

Ta funkcja to przeciążona otoka dla [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

### <a name="syntax"></a>Składnia

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda) Aby uzyskać szczegółowe informacje.

## <a name="buildroot"></a> ATLPath::BuildRoot

Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

### <a name="syntax"></a>Składnia

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota) Aby uzyskać szczegółowe informacje.

## <a name="canonicalize"></a> ATLPath::Canonicalize

Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

### <a name="syntax"></a>Składnia

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea) Aby uzyskać szczegółowe informacje.

## <a name="combine"></a> ATLPath::Combine

Ta funkcja to przeciążona otoka dla [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

### <a name="syntax"></a>Składnia

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz PathCombine.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

### <a name="syntax"></a>Składnia

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa) Aby uzyskać szczegółowe informacje.

## <a name="compactpath"></a> ATLPath::CompactPath

Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

### <a name="syntax"></a>Składnia

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha) Aby uzyskać szczegółowe informacje.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

### <a name="syntax"></a>Składnia

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa) Aby uzyskać szczegółowe informacje.

## <a name="fileexists"></a> ATLPath::FileExists

Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

### <a name="syntax"></a>Składnia

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa) Aby uzyskać szczegółowe informacje.

## <a name="findextension"></a> ATLPath::FindExtension

Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

### <a name="syntax"></a>Składnia

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona) Aby uzyskać szczegółowe informacje.

## <a name="findfilename"></a> ATLPath::FindFileName

Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

### <a name="syntax"></a>Składnia

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) Aby uzyskać szczegółowe informacje.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

### <a name="syntax"></a>Składnia

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera) Aby uzyskać szczegółowe informacje.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```
### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz PathIsDirectory.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

### <a name="syntax"></a>Składnia

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca) Aby uzyskać szczegółowe informacje.

## <a name="isprefix"></a> ATLPath::IsPrefix

Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

### <a name="syntax"></a>Składnia

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa) Aby uzyskać szczegółowe informacje.

## <a name="isrelative"></a> ATLPath::IsRelative

Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea) Aby uzyskać szczegółowe informacje.

## <a name="isroot"></a> ATLPath::IsRoot

Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota) Aby uzyskać szczegółowe informacje.

## <a name="issameroot"></a> ATLPath::IsSameRoot

Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

### <a name="syntax"></a>Składnia

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota) Aby uzyskać szczegółowe informacje.

## <a name="isunc"></a> ATLPath::IsUNC

Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca) Aby uzyskać szczegółowe informacje.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera) Aby uzyskać szczegółowe informacje.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea) Aby uzyskać szczegółowe informacje.

## <a name="makepretty"></a> ATLPath::MakePretty

Ta funkcja to przeciążona otoka dla [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

### <a name="syntax"></a>Składnia

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya) Aby uzyskać szczegółowe informacje.

## <a name="matchspec"></a> ATLPath::MatchSpec

Ta funkcja to przeciążona otoka dla [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

### <a name="syntax"></a>Składnia

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca) Aby uzyskać szczegółowe informacje.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

Ta funkcja to przeciążona otoka dla [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

### <a name="syntax"></a>Składnia

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa) Aby uzyskać szczegółowe informacje.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

Ta funkcja to przeciążona otoka dla [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

### <a name="syntax"></a>Składnia

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa) Aby uzyskać szczegółowe informacje.

## <a name="removeargs"></a> ATLPath::RemoveArgs

Ta funkcja to przeciążona otoka dla [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

### <a name="syntax"></a>Składnia

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa) Aby uzyskać szczegółowe informacje.

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

Ta funkcja to przeciążona otoka dla [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

### <a name="syntax"></a>Składnia

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha) Aby uzyskać szczegółowe informacje.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

Ta funkcja to przeciążona otoka dla [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

### <a name="syntax"></a>Składnia

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa) Aby uzyskać szczegółowe informacje.

## <a name="removeextension"></a> ATLPath::RemoveExtension

Ta funkcja to przeciążona otoka dla [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

### <a name="syntax"></a>Składnia

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona) Aby uzyskać szczegółowe informacje.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

Ta funkcja to przeciążona otoka dla [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

### <a name="syntax"></a>Składnia

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca) Aby uzyskać szczegółowe informacje.

## <a name="renameextension"></a> ATLPath::RenameExtension

Ta funkcja to przeciążona otoka dla [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

### <a name="syntax"></a>Składnia

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona) Aby uzyskać szczegółowe informacje.

## <a name="skiproot"></a> ATLPath::SkipRoot

Ta funkcja to przeciążona otoka dla [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

### <a name="syntax"></a>Składnia

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota) Aby uzyskać szczegółowe informacje.

## <a name="strippath"></a> ATLPath::StripPath

Ta funkcja to przeciążona otoka dla [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

### <a name="syntax"></a>Składnia

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha) Aby uzyskać szczegółowe informacje.

## <a name="striptoroot"></a> ATLPath::StripToRoot

Ta funkcja to przeciążona otoka dla [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

### <a name="syntax"></a>Składnia

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota) Aby uzyskać szczegółowe informacje.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

Ta funkcja to przeciążona otoka dla [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

### <a name="syntax"></a>Składnia

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa) Aby uzyskać szczegółowe informacje.

