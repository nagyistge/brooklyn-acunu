brooklyn-acunu
==============

Brooklyn deployment and management of Acunu Cassandra clusters.


### Setup 1:  Dependencies

You must either enable the snapshots repo, or have the right version of 
Brooklyn installed (code downloaded and `mvn clean install`).


### Compile

To compile brooklyn-acunu, simply `mvn clean install` in the project root.


### Setup 2:  Credentials

To run, you'll need to specify credentials for your preferred cloud.  This can be done 
in `~/.brooklyn/brooklyn.properties`:

    brooklyn.jclouds.aws-ec2.identity=AKXXXXXXXXXXXXXXXXXX
    brooklyn.jclouds.aws-ec2.credential=secret01xxxxxxxxxxxxxxxxxxxxxxxxxxx

Alternatively these can be set as shell environment parameters or JVM system properties.

Many other clouds are supported also, as well as pre-existing machines ("bring your own nodes"),
custom endpoints for private clouds, and specifying custom keys and passphrases.
For more information see:

    https://github.com/brooklyncentral/brooklyn/blob/master/docs/use/guide/defining-applications/common-usage.md#off-the-shelf-locations


### Run

To run it, either:

* Build `mvn assembly:assembly` below then follow the instructions in the generated archive

* Build `mvn clean install`, then install Brooklyn and modify the `catalog.xml` to point
    at the build brooklyn-acunu module.

After about 10 minutes, it should print out the URL of the Acunu load-balancer node.
In the meantime you can follow the progress in the Brooklyn console, usually at localhost:8081.  

To destroy the VM's provisioned, either invoke `stop` on the root of the
application in the Brooklyn console or use the management console of your
cloud.  VM's are not destroyed simply by killing Brooklyn.


### Executable Assembly

This project can also build a binary redistributable by using mvn assembly:assembly.
See the source files under `src/main/assembly` for more information.  These can 
easily be modified for a custom archive.


### More about Brooklyn

Brooklyn is a code library and framework for managing distributed applications
in the cloud.  It has been used to create this project for rolling out Acunu,
as well as a number of other Big Data and complex applications.

This project can be extended for more complex topologies (such as multi-region, using a Fabric), 
additional applications which run alongside Acunu (such as Flume), and to develop 
sophisticated management policies to scale or tune the cluster for specific applications.

For more information consider:

* Visiting the open-source Brooklyn home page at  http://brooklyncentral.github.com
* Forking the Brooklyn project at  http://github.com/brooklyncentral/brooklyn
* Forking the brooklyn-acunu project at  http://github.com/cloudsoft/brooklyn-acunu
* Emailing  brooklyn-users@googlegroups.com 

For commercial enquiries -- including bespoke development and paid support --
contact Cloudsoft, the supporters of Brooklyn, at:

* www.cloudsoftcorp.com
* info@cloudsoftcorp.com

---

&copy; 2013 Cloudsoft Corporation Limited. All rights reserved.

Use of this software is subject to the Cloudsoft EULA, provided in LICENSE.md and at

http://www.cloudsoftcorp.com/cloudsoft-developer-license

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
