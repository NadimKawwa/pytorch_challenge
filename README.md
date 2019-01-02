
</form>
        <!-- '"` --><!-- </textarea></xmp> --></option></form><form class="inline-form" action="/udacity/deep-learning-v2-pytorch/delete/master/README.md" accept-charset="UTF-8" method="post"><input name="utf8" type="hidden" value="&#x2713;" /><input type="hidden" name="authenticity_token" value="+E81CwzrGBmgis9OdippvYQpDC/H1yrZteV1OvIXPgCxwOS9Nm8OvBm7d0Q/mcLx+iWSBBxm1Rb6AsGAZUCl1A==" />
          <button class="btn-octicon btn-octicon-danger tooltipped tooltipped-nw" type="submit"
            aria-label="Delete the file in your fork of this project" data-disable-with>
            <svg class="octicon octicon-trashcan" viewBox="0 0 12 16" version="1.1" width="12" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M11 2H9c0-.55-.45-1-1-1H5c-.55 0-1 .45-1 1H2c-.55 0-1 .45-1 1v1c0 .55.45 1 1 1v9c0 .55.45 1 1 1h7c.55 0 1-.45 1-1V5c.55 0 1-.45 1-1V3c0-.55-.45-1-1-1zm-1 12H3V5h1v8h1V5h1v8h1V5h1v8h1V5h1v9zm1-10H2V3h9v1z"/></svg>
          </button>
</form>  </div>

  <div class="file-info">
      164 lines (113 sloc)
      <span class="file-info-divider"></span>
    11 KB
  </div>
</div>


  <div id="readme" class="readme blob instapaper_body js-code-block-container">
    <article class="markdown-body entry-content" itemprop="text"><h1><a id="user-content-deep-learning-pytorch" class="anchor" aria-hidden="true" href="#deep-learning-pytorch"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Deep Learning (PyTorch)</h1>
<p>This repository contains material related to Udacity's <a href="https://github.com/udacity/deep-learning-v2-pytorch" rel="nofollow">Deep Learning with PyTorch as part of Facebook's scholarship challenge</a>. The objective is to predict the name of a flower based on flower images that are fed into a neural network. The project makes use of the <a href="https://pytorch.org" rel="nofollow">PyTorch Library</a> and its available pretrained networks. We begin by loading the data, which in this case is only the training and validation data. We then agument the images by applying transformations such as random rotation, distortions, and crops. The next step is mapping the data to the flower categories. The final objective is to create a model that takes in a random image (not necessarily a flower), processes it to be compatible with PyTorch and displays the top 5 most probable flowers with corresponding probabilities.</p>


<hr>
<h1><a id="user-content-dependencies" class="anchor" aria-hidden="true" href="#dependencies"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Dependencies</h1>
<h2><a id="user-content-configure-and-manage-your-environment-with-anaconda" class="anchor" aria-hidden="true" href="#configure-and-manage-your-environment-with-anaconda"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Configure and Manage Your Environment with Anaconda</h2>
<p>Per the Anaconda <a href="http://conda.pydata.org/docs" rel="nofollow">docs</a>:</p>
<blockquote>
<p>Conda is an open source package management system and environment management system
for installing multiple versions of software packages and their dependencies and
switching easily between them. It works on Linux, OS X and Windows, and was created
for Python programs but can package and distribute any software.</p>
</blockquote>
<h2><a id="user-content-overview" class="anchor" aria-hidden="true" href="#overview"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Overview</h2>
<p>Using Anaconda consists of the following:</p>
<ol>
<li>Install <a href="http://conda.pydata.org/miniconda.html" rel="nofollow"><code>miniconda</code></a> on your computer, by selecting the latest Python version for your operating system. If you already have <code>conda</code> or <code>miniconda</code> installed, you should be able to skip this step and move on to step 2.</li>
<li>Create and activate * a new <code>conda</code> <a href="http://conda.pydata.org/docs/using/envs.html" rel="nofollow">environment</a>.</li>
</ol>
<p>* Each time you wish to work on any exercises, activate your <code>conda</code> environment!</p>
<hr>
<h2><a id="user-content-1-installation" class="anchor" aria-hidden="true" href="#1-installation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>1. Installation</h2>
<p><strong>Download</strong> the latest version of <code>miniconda</code> that matches your system.</p>
<table>
<thead>
<tr>
<th></th>
<th>Linux</th>
<th>Mac</th>
<th>Windows</th>
</tr>
</thead>
<tbody>
<tr>
<td>64-bit</td>
<td><a href="https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh" rel="nofollow">64-bit (bash installer)</a></td>
<td><a href="https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh" rel="nofollow">64-bit (bash installer)</a></td>
<td><a href="https://repo.continuum.io/miniconda/Miniconda3-latest-Windows-x86_64.exe" rel="nofollow">64-bit (exe installer)</a></td>
</tr>
<tr>
<td>32-bit</td>
<td><a href="https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86.sh" rel="nofollow">32-bit (bash installer)</a></td>
<td></td>
<td><a href="https://repo.continuum.io/miniconda/Miniconda3-latest-Windows-x86.exe" rel="nofollow">32-bit (exe installer)</a></td>
</tr>
</tbody>
</table>
<p><strong>Install</strong> <a href="http://conda.pydata.org/miniconda.html" rel="nofollow">miniconda</a> on your machine. Detailed instructions:</p>
<ul>
<li><strong>Linux:</strong> <a href="http://conda.pydata.org/docs/install/quick.html#linux-miniconda-install" rel="nofollow">http://conda.pydata.org/docs/install/quick.html#linux-miniconda-install</a></li>
<li><strong>Mac:</strong> <a href="http://conda.pydata.org/docs/install/quick.html#os-x-miniconda-install" rel="nofollow">http://conda.pydata.org/docs/install/quick.html#os-x-miniconda-install</a></li>
<li><strong>Windows:</strong> <a href="http://conda.pydata.org/docs/install/quick.html#windows-miniconda-install" rel="nofollow">http://conda.pydata.org/docs/install/quick.html#windows-miniconda-install</a></li>
</ul>
<h2><a id="user-content-2-create-and-activate-the-environment" class="anchor" aria-hidden="true" href="#2-create-and-activate-the-environment"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>2. Create and Activate the Environment</h2>
<p>For Windows users, these following commands need to be executed from the <strong>Anaconda prompt</strong> as opposed to a Windows terminal window. For Mac, a normal terminal window will work.</p>
<h4><a id="user-content-git-and-version-control" class="anchor" aria-hidden="true" href="#git-and-version-control"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Git and version control</h4>
<p>These instructions also assume you have <code>git</code> installed for working with Github from a terminal window, but if you do not, you can download that first with the command:</p>
<pre><code>conda install git
</code></pre>
<p>If you'd like to learn more about version control and using <code>git</code> from the command line, take a look at our <a href="https://www.udacity.com/course/version-control-with-git--ud123" rel="nofollow">free course: Version Control with Git</a>.</p>
<p><strong>Now, we're ready to create our local environment!</strong></p>
<ol>
<li>Clone the repository, and navigate to the downloaded folder. This may take a minute or two to clone due to the included image data.</li>
</ol>
<pre><code>git clone https://github.com/udacity/deep-learning-v2-pytorch.git
cd deep-learning-v2-pytorch
</code></pre>
<ol start="2">
<li>
<p>Create (and activate) a new environment, named <code>deep-learning</code> with Python 3.6. If prompted to proceed with the install <code>(Proceed [y]/n)</code> type y.</p>
<ul>
<li><strong>Linux</strong> or <strong>Mac</strong>:</li>
</ul>
<pre><code>conda create -n deep-learning python=3.6
source activate deep-learning
</code></pre>
<ul>
<li><strong>Windows</strong>:</li>
</ul>
<pre><code>conda create --name deep-learning python=3.6
activate deep-learning
</code></pre>
<p>At this point your command line should look something like: <code>(deep-learning) &lt;User&gt;:deep-learning-v2-pytorch &lt;user&gt;$</code>. The <code>(deep-learning)</code> indicates that your environment has been activated, and you can proceed with further package installations.</p>
</li>
<li>
<p>Install PyTorch and torchvision; this should install the latest version of PyTorch.</p>
<ul>
<li><strong>Linux</strong> or <strong>Mac</strong>:</li>
</ul>
<pre><code>conda install pytorch torchvision -c pytorch
</code></pre>
<ul>
<li><strong>Windows</strong>:</li>
</ul>
<pre><code>conda install pytorch -c pytorch
pip install torchvision
</code></pre>
</li>
<li>
<p>Install a few required pip packages, which are specified in the requirements text file (including OpenCV).</p>
</li>
</ol>
<pre><code>pip install -r requirements.txt
</code></pre>
<ol start="7">
<li>That's it!</li>
</ol>
<p>Now most of the <code>deep-learning</code> libraries are available to you. Very occasionally, you will see a repository with an addition requirements file, which exists should you want to use TensorFlow and Keras, for example. In this case, you're encouraged to install another library to your existing environment, or create a new environment for a specific project.</p>
<p>Noe, assuming your <code>deep-learning</code> environment is still activated, you can navigate to the main repo and start looking at the notebooks:</p>
<pre><code>cd
cd deep-learning-v2-pytorch
jupyter notebook
</code></pre>
<p>To exit the environment when you have completed your work session, simply close the terminal window.</p>
</article>
  </div>
