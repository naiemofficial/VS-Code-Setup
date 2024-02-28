# VS Code Setup
![Visual-Studio-Code-BG-min](https://github.com/naiemofficial/VS-Code-Setup/assets/34242279/5e25dad7-ce6b-44d7-ade9-dc92769b885f)

### Fresh Coding Environment
<hr>
</p>During the build and run of a program like C, C++, Java, there comes some new file with the same name like <code>filename</code>, <code>filename.exe</code> or any other name. Which is also called <b>Executable Code</b>.  It looks messy when there so many programs in one folder. To keep it clean and fresh, we can move or keep the executable file to another folder location. See below how we can do this for different operating systems. Make sure you have installed <a href="https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner" target="_blank"><sub><img height="18px" src="https://user-images.githubusercontent.com/34242279/157722497-db7e3df1-b593-4175-8557-614046fa4cc7.png"><img src="https://formulahendry.gallerycdn.vsassets.io/extensions/formulahendry/code-runner/0.12.1/1696752986258/Microsoft.VisualStudio.Services.Icons.Default" width="50px"/></sub> Code Runner</a> extension and <code>compiler</code>.</p>
<table>
	<thead>
    	<th width="300px" align="center" valign="center">Platform</th>
		<th width="1000px" align="center" valign="center"></th>
  	</thead>
	<tbody>
		<td width="300px" align="center" valign="top">
			<img width="150px" src="https://lh3.googleusercontent.com/u/0/d/1qdR4kJ0lzBaSIfHYQ5rZzqHzaGq1X27i=w1333-h656-iv1"/>
			<p><b>Linux</b></p>
		</td>
		<td width="1000px" align="left" valign="top">
			<ol>
				<li>Create a folder named <code>temp</code> in a different folder location. For to be more more specific I'm creating folder and sub-folder like <code>temp</code>/<code>Programming</code>/<code>cpp</code> <sub><sup>(Here <code>cpp</code> for <code>c++</code> program, you can add folder named <code>c</code> if you're gonna setup it for c-program or any other name whatever you prefer)</sup></sub>. let's assume after creating the folder the <b>path / temporary path</b> is <code>/temp/Programming/cpp/</code><br><br></li>
				<li>Open <b>VS Code</b> and go to <code>Settings</code>, then open the <code>Settings</code> as JSON<br><br></li>
				<li>Find the object that named <code>code-runner.executorMap</code>, then find the object-key named <code>cpp</code> <sub><sup>(as we're doing this c++ program)</sup></sub><br><br></li>
				<li>
					Now edit the object-key value as following - <br>
					<code>cd current_dirrectory && compiler_name "<b>filename</b>" -o "temporary_path/<b>executable_filename</b>" && "temporary_path/<b>executable_filename</b>"</code>
					<br><br>
					Here - <br>
					<ul>
						<li><b>current_dirrectory: </b> <code>$dir</code></li>
						<li><b>compiler_name: </b> <code>g++</code></li>
						<li>
							<b>filename: </b> <code>$fileName</code> 
							<sub><sup>(Note: Wrapping <ins><b>filename</b></ins> by qutoations will allow to use space in the file name e.g. <ins>Hello World.cpp</ins>)</sup></sub>
						</li>
						<li><b>temporary_path: </b> <code>/temp/Programming/cpp/</code></li>
						<li><b>executable_filename: </b> <code>$fileNameWithoutExt</code></li>
					</ul>
					<br><br>
					So the value will be as below - <br>
					<code>cd $dir && g++ "<b>$fileName</b>" -o "/temp/Programming/cpp/<b>$fileNameWithoutExt</b>" && "/temp/Programming/cpp/<b>$fileNameWithoutExt</b>"</code>
					<br><br>
					To convert it as JSON value, the final result will be as below - <br>
					<code>"cd $dir && g++ \"$fileName\" -o \"/temp/Programming/cpp/$fileNameWithoutExt\" && \"/temp/Programming/cpp/$fileNameWithoutExt\""</code>
					<br><br>
					or, copy the full-line from the below -
				</li>
			</ol>
		</td>
	</tbody>
</table>

```json
"cpp": "cd $dir && g++ \"$fileName\" -o \"/temp/Programming/cpp/$fileNameWithoutExt\" && \"/temp/Programming/cpp/$fileNameWithoutExt\""
```




<br><br>
### Setup for CP
<p>Add external input & output file: (setup for Linux)</p>
<hr>
<ol>
	<li>Create a folder with the name <code>.vscode</code> in your VS Code workspace. If the folder already exists then nothing to do. <sub><sup>(It's not necessary to keep <code>input.txt</code>, <code>output.txt</code> file in the <code>.vscode</code> folder.)</sup></sub> 
	<li>Create a file with the name <code>input.txt</code> inside <code>.vscode</code> folder.</li>
	<li>Create a file with the name <code>output</code> inside <code>.vscode</code> folder.</li>
	<li>Create a file with the name <code>settings.json</code> inside the <code>.vscode</code> folder. If the file already exists then no need to create</li>
	<li>In the <code>settings.json</code> and go to <code>Settings</code>, then open the <code>Settings</code> as JSON<br><br></li>
	<li>Find the object that named <code>code-runner.executorMap</code>, if the object isn't there then add it <code>code-runner.executorMap</code></li>
	<li>find the object-key named <code>cpp</code> <sub><sup>(as we're doing this c++ program)</sup></sub>, if the object-key isn't there then add it <code>"cpp": value</code><br><br></li>
	<li>Now edit the object-key value, copy the below code and paste it after <b>executable_filename</b> or before ending the JSON value wrapping quotations  </li>
</ol>

```
 < \".vscode/input.txt\" > \".vscode/output.txt\""
```

or, Copy the full-line

```json
"cpp": "cd $dir && g++ \"$fileName\" -o \"$fileNameWithoutExt\" && \"$fileNameWithoutExt\" < \".vscode/input.txt\" > \".vscode/output.txt\""
```

If you applied the <a href="#fresh-coding-environment"><b><ins>Fresh Coding Environment</ins></b></a> process, the can copy and paste the below code

```json
"cpp": "cd $dir && g++ \"$fileName\" -o \"/temp/Programming/cpp/$fileNameWithoutExt\" && \"/temp/Programming/cpp/$fileNameWithoutExt\" < \".vscode/input.txt\" > \".vscode/output.txt\""
```

<br><br>

#### Demo
![settings json](https://github.com/naiemofficial/VS-Code-Setup/assets/34242279/ddf4775c-d688-45ad-9619-02c0dd58b0b1)
![VS Code Tutorial cpp](https://github.com/naiemofficial/VS-Code-Setup/assets/34242279/9557d875-c861-4022-9733-2d6c163337c2)

