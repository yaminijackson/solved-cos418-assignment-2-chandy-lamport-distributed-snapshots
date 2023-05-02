Download Link: https://assignmentchef.com/product/solved-cos418-assignment-2-chandy-lamport-distributed-snapshots
<br>
<h2><a id="user-content-introduction" class="anchor" href="https://github.com/theoliao1998/Distributed-Systems/tree/master/2%20Chandy-Lamport%20Distributed%20Snapshots#introduction" aria-hidden="true"></a>Introduction</h2>

In this assignment you will implement the <a href="https://github.com/theoliao1998/Distributed-Systems/blob/master/2%20Chandy-Lamport%20Distributed%20Snapshots/papers/chandy_lamport.pdf">Chandy-Lamport algorithm</a> for distributed snapshots. Your snapshot algorithm will be implemented on top of a token passing system, similar to the ones presented in <a href="https://github.com/theoliao1998/Distributed-Systems/blob/master/2%20Chandy-Lamport%20Distributed%20Snapshots/docs/P4-distributed-snapshots.zip">Precept 4</a> and in the Chandy-Lamport paper.

The algorithm makes the following assumptions:

<ul>

 <li>There are no failures and all messages arrive intact and only once</li>

 <li>The communication channels are unidirectional and FIFO ordered</li>

 <li>There is a communication path between any two processes in the system</li>

 <li>Any process may initiate the snapshot algorithm</li>

 <li>The snapshot algorithm does not interfere with the normal execution of the processes</li>

 <li>Each process in the system records its local state and the state of its incoming channels</li>

</ul>

<h2><a id="user-content-software" class="anchor" href="https://github.com/theoliao1998/Distributed-Systems/tree/master/2%20Chandy-Lamport%20Distributed%20Snapshots#software" aria-hidden="true"></a>Software</h2>

You will find the code under this directory. The code is organized as follows:

<ul>

 <li><tt>server.go</tt>: A process in the distributed algorithm</li>

 <li><tt>simulator.go</tt>: A discrete time simulator</li>

 <li><tt>logger.go</tt>: A logger that records events executed by system (useful for debugging)</li>

 <li><tt>common.go</tt>: Debug flag and common message types used in the server, logger, and simulator</li>

 <li><tt>snapshot_test.go</tt>: Tests you need to pass</li>

 <li><tt>syncmap.go</tt>: Implementation of thread-safe map</li>

 <li><tt>queue.go</tt>: Simple queue interface implemented using lists in Go</li>

 <li><tt>test_common.go</tt>: Helper functions for testing</li>

 <li><tt>test_data/</tt>: Test case inputs and expected results</li>

</ul>

Of these files, you only need to turn in <tt>server.go</tt> and <tt>simulator.go</tt>. However, some other files also contain information that will be useful for your implementation or debugging, such as the <tt>debug</tt> flag in <tt>common.go</tt> and the thread-safe map in <tt>syncmap.go</tt>. Your task is to implement the functions that say <tt>TODO: IMPLEMENT ME</tt>, adding fields to the surrounding classes if necessary.

<h3><a id="user-content-testing" class="anchor" href="https://github.com/theoliao1998/Distributed-Systems/tree/master/2%20Chandy-Lamport%20Distributed%20Snapshots#testing" aria-hidden="true"></a>Testing</h3>

Our grading uses the tests in <tt>snapshot_test.go</tt> provided to you. Test cases can be found in <tt>test_data/</tt>. To test the correctness of your code, simply run the following command:

<pre>  $ cd chandy-lamport/  $ go test  Running test '2nodes.top', '2nodes-simple.events'  Running test '2nodes.top', '2nodes-message.events'  Running test '3nodes.top', '3nodes-simple.events'  Running test '3nodes.top', '3nodes-bidirectional-messages.events'  Running test '8nodes.top', '8nodes-sequential-snapshots.events'  Running test '8nodes.top', '8nodes-concurrent-snapshots.events'  Running test '10nodes.top', '10nodes.events'  PASS  ok      _/path/to/chandy-lamport 0.012s</pre>

To run individual tests, you can look up the test names in <tt>snapshot_test.go</tt> and run:

<pre>  $ go test -run 2Node  Running test '2nodes.top', '2nodes-simple.events'  Running test '2nodes.top', '2nodes-message.events'  PASS  ok      chandy-lamport  0.006s</pre>


