# Base Directories

> [!TIP]
> Use `macos_asposix=True` to return POSIX directory on macOS.

<table>
  <thead>
    <tr>
      <th>Function</th>
      <th>POSIX</th>
      <th>macOS</th>
      <th>Windows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>cache_dir()</code></td>
      <td>$XDG_CACHE_HOME (default: ~/.cache)</td>
      <td>~/Library/Caches</td>
      <td>FOLDERID_LocalAppData</td>
    </tr>
    <tr>
      <td><code>cache_dir(system=True)</code></td>
      <td>/var/cache</td>
      <td>/Library/Caches</td>
      <td>FOLDERID_ProgramData</td>
    </tr>
    <tr>
      <td><code>config_dir()</code></td>
      <td>$XDG_CONFIG_HOME (default: ~/.config)</td>
      <td>~/Library/Application Support</td>
      <td>FOLDERID_RoamingAppData</td>
    </tr>
    <tr>
      <td><code>config_dir(system=True)</code></td>
      <td>/etc</td>
      <td rowspan=2>/Library/Application Support</td>
      <td rowspan=2>FOLDERID_ProgramData</td>
    </tr>
    <tr>
      <td><code>config_dir(system=True, posix_local=True)</code></td>
      <td>/usr/local/etc</td>
    </tr>
    <tr>
      <td><code>data_dir()</code></td>
      <td rowspan=2>$XDG_DATA_HOME (default: ~/.local/share)</td>
      <td rowspan=2>~/Library/Application Support</td>
      <td>FOLDERID_RoamingAppData</td>
    </tr>
    <tr>
      <td><code>data_dir(windows_roaming=False)</code></td>
      <td>FOLDERID_LocalAppData</td>
    </tr>
    <tr>
      <td><code>data_dir(system=True)</code></td>
      <td>/usr/share</td>
      <td rowspan=2>/Library/Application Support</td>
      <td rowspan=2>FOLDERID_ProgramData</td>
    </tr>
    <tr>
      <td><code>data_dir(system=True, posix_local=True)</code></td>
      <td>/usr/local/share</td>
    </tr>
    <tr>
      <td><code>log_dir()</code></td>
      <td>$XDG_STATE_HOME (default: ~/.local/state)</td>
      <td>~/Library/Logs</td>
      <td>FOLDERID_LocalAppData</td>
    </tr>
    <tr>
      <td><code>log_dir(system=True)</code></td>
      <td>/var/log</td>
      <td>/Library/Logs</td>
      <td>FOLDERID_ProgramData</td>
    </tr>
    <tr>
      <td><code>system_config_dirs()</code></td>
      <td>[/usr/local/etc, /etc]</td>
      <td rowspan=2>[/Library/Application Support]</td>
      <td rowspan=2>[FOLDERID_ProgramData]</td>
    </tr>
    <tr>
      <td><code>system_config_dirs(posix_xdg=True)</code></td>
      <td>$XDG_CONFIG_DIRS (default: [/etc/xdg])</td>
    </tr>
    <tr>
      <td><code>system_data_dirs()</code></td>
      <td>[/usr/local/share, /usr/share]</td>
      <td rowspan=2>[/Library/Application Support]</td>
      <td rowspan=2>[FOLDERID_ProgramData]</td>
    </tr>
    <tr>
      <td><code>system_data_dirs(posix_xdg=True)</code></td>
      <td>$XDG_DATA_DIRS (default: [/usr/local/share, /usr/share])</td>
    </tr>
  </tbody>
</table>

# User Directories

<table>
  <thead>
    <tr>
      <th>Function</th>
      <th>POSIX</th>
      <th>macOS</th>
      <th>Windows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>home_dir()</code></td>
      <td colspan=2>$HOME (fallback: <code>pw_dir</code>)</td>
      <td>FOLDERID_Profile</td>
    </tr>
    <tr>
      <td><code>desktop_dir()</code></td>
      <td>$XDG_DESKTOP_DIR</td>
      <td>~/Desktop</td>
      <td>FOLDERID_Desktop</td>
    </tr>
    <tr>
      <td><code>documents_dir()</code></td>
      <td>$XDG_DOCUMENTS_DIR</td>
      <td>~/Documents</td>
      <td>FOLDERID_Documents</td>
    </tr>
    <tr>
      <td><code>downloads_dir()</code></td>
      <td>$XDG_DOWNLOAD_DIR</td>
      <td>~/Downloads</td>
      <td>FOLDERID_Downloads</td>
    </tr>
    <tr>
      <td><code>music_dir()</code></td>
      <td>$XDG_MUSIC_DIR</td>
      <td>~/Music</td>
      <td>FOLDERID_Music</td>
    </tr>
    <tr>
      <td><code>pictures_dir()</code></td>
      <td>$XDG_PICTURES_DIR</td>
      <td>~/Pictures</td>
      <td>FOLDERID_Pictures</td>
    </tr>
    <tr>
      <td><code>public_dir()</code></td>
      <td>$XDG_PUBLICSHARE_DIR</td>
      <td>~/Public</td>
      <td>FOLDERID_Public</td>
    </tr>
    <tr>
      <td><code>videos_dir()</code></td>
      <td>$XDG_VIDEOS_DIR</td>
      <td>~/Movies</td>
      <td>FOLDERID_Videos</td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> The fallback for *unset* $XDG_*_DIR is chosen to be the home directory. Adapted from [disabled user directories](https://freedesktop.org/wiki/Software/xdg-user-dirs/#:~:text=Note%3A%20To%20disable%20a%20directory%2C%20point%20it%20to%20the%20homedir%2E).

# Application Directories

<table>
  <thead>
    <tr>
      <th>Method</th>
      <th>POSIX</th>
      <th>macOS</th>
      <th>Windows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>self.cache_dir(...)</code></td>
      <td colspan=2><code>cache_dir(...)</code>/<code>self.app_name</code></td>
      <td><code>cache_dir(...)</code>/<code>self.app_name</code>/Caches</td>
    </tr>
    <tr>
      <td><code>self.config_dir(...)</code></td>
      <td colspan=2><code>config_dir(...)</code>/<code>self.app_name</code></td>
      <td><code>config_dir(...)</code>/<code>self.app_name</code>/Settings</td>
    </tr>
    <tr>
      <td><code>self.data_dir(...)</code></td>
      <td colspan=3><code>data_dir(...)</code>/<code>self.app_name</code></td>
    </tr>
    <tr>
      <td><code>self.log_dir(...)</code></td>
      <td colspan=2><code>log_dir(...)</code>/<code>self.app_name</code></td>
      <td><code>log_dir(...)</code>/<code>self.app_name</code>/Logs</td>
    </tr>
    <tr>
      <td><code>self.system_config_dirs(...)</code></td>
      <td colspan=2><code>system_config_dirs(...)</code>/<code>self.app_name</code></td>
      <td><code>system_config_dirs(...)</code>/<code>self.app_name</code>/Settings</td>
    </tr>
    <tr>
      <td><code>self.system_data_dirs(...)</code></td>
      <td colspan=3><code>system_data_dirs(...)</code>/<code>self.app_name</code></td>
    </tr>
  </tbody>
</table>
