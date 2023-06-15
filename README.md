# anomalish

An One-way [MyAnimeList][mal] -> [Shikimori][shiki] List Updater, written in PowerShell.

## Motivation

I (nattadasu) personally used [MyAniLi by infanf][mali] to sync my anime lists
to several anime trackers, but it does not support Shikimori due to ongoing
conflict, which is understable. So I decided to write my own script to do that
by checking RSS feed of MyAnimeList then update Shikimori if there is any
changes.

I didn't write the script in Python because at the time of writing, I'm nearly
forget how to write PowerShell script, so I decided to write it in PowerShell
to refresh my memory. :D

Although, yes, using PowerShell could possibly make the script less portable, so
Python version (or even other languages) might be written in the future.

### Why one-way?

Because I don't want to mess up my MyAnimeList list by updating it from
Shikimori, as my main anime list is on MyAnimeList and my main sync app is
MyAniLi.

### Fun facts

1. Did you know that Shikimori entry ID is actually interchangeable with
   MyAnimeList entry ID? For example, [Shikimori entry ID 38000][shiki-1] is
   [MyAnimeList entry ID 38000][mal-1]. However, this is not always the case, as
   some entries have unique prefix in Shikimori's end, and this script will try
   to mitigate that automatically.

2. Did you know that Shikimori has English version? Simply login to your account,
   open "⚙️ Настройки" (gear icon) on the top right, then select "English" on
   "Язык интерфейса" (Interface language) option.

3. Did you know the project name, `anomalish`, is a synonym of the project's
   tagline?

## Usage

> **Note**: These steps will assume that you're already understand how to use
> basic shell/PowerShell commands. If you don't, please learn it first.

0. Install [PowerShell Core][ps] and [Git][git] if you haven't already.
1. Clone this repository to your computer.
2. Open PowerShell Core and `cd` to the cloned repository.
   * If you're using Windows, you can open PowerShell Core by right-clicking
     on the cloned repository folder while holding `Shift` key, then select
     `Open PowerShell window here`.
   * Or, in terminal or command prompt, type `cd` then drag the cloned
     repository folder to the terminal/command prompt window, then press
     `Enter`. Then, type `pwsh` and press `Enter`.
3. For Windows, set execution policy to allow running unsigned scripts by typing
   `Set-ExecutionPolicy -ExecutionPolicy Unrestricted` and press `Enter`.
4. Copy `config.example.json` to `config.json` by typing
   `Copy-Item -Path config.example.json -Destination config.json` and press
   `Enter`.
5. Open `config.json` with your favorite text editor and fill in the required
   information.
   * For Shikimori, create a new application at [Shikimori's API page][shiki-api],
     click on `create`/`создать` link. Configure as follows:
     * Название/Name: *any name you want*
     * Картинка/Image (optional): *any image you want*
     * Redirect URI: `urn:ietf:wg:oauth:2.0:oob`, must be exactly like this.
     * Scopes:
       * [x] user\_rates
     * Описание/Description (optional): *any description you want*
   * Copy Client ID, Client Secret, Client Name (Application Name), and
     Redirect URI to `config.json`.
     * If Shikimori did not redirect you to the page with Client ID and Client
       Secret, you can find it at [Shikimori's API page][shiki-api] by clicking
       on the application you created.
   * For MyAnimeList, simply fill in your username.

<!-- ref -->
[mal]: https://myanimelist.net/
[shiki]: https://shikimori.me/
[mali]: https://myani.li/
[ps]: https://github.com/PowerShell/PowerShell
[git]: https://git-scm.com/
[shiki-api]: https://shikimori.me/oauth/applications
[shiki-1]: https://shikimori.me/animes/38000
[mal-1]: https://myanimelist.net/anime/38000
