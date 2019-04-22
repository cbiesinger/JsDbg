# Installation instructions


1. Download the [x64 .NET Core SDK Binary](https://dotnet.microsoft.com/download)
2. In this checkout in `server/JsDbg.Gdb`, run `dotnet publish -c Release -r linux-x64`
3. Edit server/JsDbg.Gdb/JsDbg.py, change the paths to be correct. extensions needs to point to the extensions folder in this checkout and exec path needs to point to the `JsDbg.Gdb.Gdb` binary that the publish command installed above.
4. Edit your `~/.gdbinit` to add (update the path as appropriate for the directory in the checkout):
```
python
sys.path.insert(0, ".../JsDbg/server/JsDbg.Gdb")
import JsDbg
end
set pagination off
```
5. Type `jsdbg` at your gdb prompt whenever you're ready to start the JsDbg webserver
6. Run gdb with your `chrome` or `content_shell` binary, break somewhere, and load [http://localhost:50000](http://localhost:50000)!
